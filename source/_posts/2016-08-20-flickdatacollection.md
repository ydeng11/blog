---
title: 如何在Flickr收集有地理信息的数据
date: 2016-08-20 01:04:45
tags: 
- Data Mining
- Spider
- Python
categories: 编程
---


>Sharp tools make good work.

在社交数据的收集中，关于收集twitter上数据的教程已经很多了，但是关于Flickr数据收集的教程还挺少。最近正好要收集Flickr上的数据，就去研究了下，现在把过程发出来给大家看看。

## 申请API
Flickr 提供了对应不同语言的API供开发者使用，具体内容可以去[使用文档](https://www.flickr.com/services/api/)查询。
在这里我使用了[python-flickr-api](https://github.com/alexis-mignon/python-flickr-api/)。在使用Flickr 的API时，有些功能要求使用者提供API key和Secret token. 申请过程非常简单，只要去这个[网址](https://www.flickr.com/services/apps/create/apply)申请即可。
<!-- more -->

## 爬取区域照片信息
我在这里使用了flickr.photos.search去搜索一片区域的照片。在这里需要注意，我们每一次query只能从Flickr得到最多4000张的不重复照片。因此在区域过大时，我们需要做些处理来尽可能地收集到所有数据。我在这里将收集区域分成了100个小的地块进行收集，但其实也可以选择多个中心点，并设置一个半径来进行组合。

```
bboxlist.py
```
```python
class getbboxList:
	def __init__(self):
		self.bbox = "-80.316151, 25.706852, -80.118397, 25.855552"
		self.bottomleft_x = 25.706852
		self.bottomleft_y = -80.316151
		self.upright_x = 25.855552
		self.upright_y = -80.118397
		#divide the area into 100 boxes but we just need 81 points to get all the boxes
	def splitArea(self):
		diffy = (self.upright_y - self.bottomleft_y)/9
		diffx = (self.upright_x - self.bottomleft_x)/9
		# print diff
		x = []
		y = []
		for i in range(9):
			# print i
			x.append(i*diffy + self.bottomleft_y)

		for i in range(9):
			# print i
			y.append(i*diffx + self.bottomleft_x)

		bboxT = []
		for xx in x:
			for yy in y:
				# print xx,yy
				bboxT.append([xx,yy])
		bboxlist = []

		for i in range(len(bboxT)):
			# print type(bbox1[i])
			y1 = bboxT[i][0]
			x1 = bboxT[i][1]
			y2 = bboxT[i][0] + diffy
			x2 = bboxT[i][1] + diffx
			bboxlist.append([y1,x1,y2,x2])
			# bbox2 = bbox1[i] + [diffx, diffy]
			# print bbox2
		print "The area has been divided into 100 boxes"
		return bboxlist

# test = bboxList()
# bboxlist = test.splitArea()
# for i in bboxlist:
# 	print type(str(i))

```
## 爬取照片信息并存入mysql
我使用了flickr.photos.getInfor去爬取每张搜索到的照片的信息，并把信息存入到mysql。

```python
# -*- coding:utf-8 -*-
import flickr_api
from flickr_api.api import flickr
import json
import MySQLdb
from datetime import datetime
from datetime import timedelta
import sys
import bboxList
reload(sys)
sys.setdefaultencoding('utf-8')

class flickrDataCollection:
	def __init__(self):
		bboxlist = bboxList.getbboxList()
		my_api_key = 'your api key'
		my_secret = 'your token'
		flickr_api.set_keys(api_key = my_api_key, api_secret = my_secret)
		auth = flickr_api.auth.AuthHandler() #creates the AuthHandler object

		self.bbox = "-80.316151, 25.706852, -80.118397, 25.855552" #The leftbottom and upright cornor of area
		self.bboxlist = bboxlist.splitArea()
		self.accuracy = 16 #street level
		self.content_type = 1 #photos only
		self.per_page = 500 #the number of data in each page
		self.page = 500 # the maximum is 500
		self.start_date = "2005-08-01" #start date
		self.end_date = "2016-08-01" #end-date
		self.table = "flickr_data"

	
	def getPhotos(self, parameter):
		# print flickr.photos.geo.getLocation()
		geoPhotos = flickr.photos.search(bbox=parameter["bbox"], accuracy=parameter["accuracy"],content_type=parameter["content_type"],
									per_page = parameter["per_page"], page =parameter["page"], min_taken_date = parameter["bbox"],
									max_taken_date = parameter["max_taken_date"], format='json')
		# test = xmltodict.parse(geoPhotos)
		# print test.values()
		# print geoPhotos
		id_list = []
		geoPhotos = geoPhotos.lstrip("jsonFlickrApi(")
		geoPhotos = geoPhotos.rstrip(")")
		# print geoPhotos
		parsed_text = json.loads(geoPhotos)
		# print type(parsed_text['photos']['photo'])
		for photo in parsed_text['photos']['photo']:
			id_list.append(photo['id'])
			print "The photo %s is found." %photo['id']
		return id_list

#get the information and location of photos
	def getInfo(self,photoId):
		tag = []
		text = flickr.photos.getInfo(photo_id=photoId, format='json')
		text = text.lstrip('jsonFlickrApi(')
		text = text.rstrip(')')
		parsed_data = json.loads(text)
		text_tag = parsed_data['photo']['tags']['tag']
		for line in text_tag:
			tag.append(line['_content'])
		longitude = parsed_data['photo']['location']['longitude']
		latitude = parsed_data['photo']['location']['latitude']
		time = parsed_data['photo']['dates']['taken']
		url_loc = parsed_data['photo']['urls']['url']
		url = url_loc[0]['_content']
		try:
			location = parsed_data['photo']['location']['locality']['_content']
		except:
			Exception
			location = []
		title = parsed_data['photo']['title']['_content']
		photo_id = parsed_data['photo']['id']
		info = {
				"photo_id":photo_id,
				"title":title,
				"tag":tag,
				"taken_time":time,
				"coordinates": (latitude, longitude),
				'location':location,
				'url':url
		}
		print "The information of photo %s is collected." %photo_id
		return info

	def savetomysql(self, table, data):
		try:
			db = MySQLdb.connect('host','user','password','database')
			cur = db.cursor()
		except MySQLdb.Error, e:
			print "The error found in connnecting database%d: %s" % (e.args[0], e.args[1])
		try:
			db.set_character_set('utf8')
			cols = ', '.join(str(v) for v in data.keys())
			values = '"'+'","'.join(str(v) for v in data.values())+'"'
			sql = "INSERT INTO %s (%s) VALUES (%s) ON DUPLICATE KEY UPDATE %s=%s" % (table, cols, values, 'photo_id', 'photo_id') #the primary key is photo_id
			# print sql
			try:
				result = cur.execute(sql)
				db.commit()
				#Check the result of command execution
				if result:
					print "This data is imported into database."
				else:
					return 0
			except MySQLdb.Error,e:
				 #rollback if error
				db.rollback()
				 #duplicate primary key
				if "key 'PRIMARY'" in e.args[1]:
					print "Data Existed"
				else:
					print "Insertion faied, reason is %d: %s" % (e.args[0], e.args[1])
		except MySQLdb.Error,e:
			print "Error found in database, reason is %d: %s" % (e.args[0], e.args[1])

	def main(self):
		format_time = "%Y-%m-%d" 
		# auth.set_verifier = '72157671561687371-cbb80beb464db307'
		# flickr_api.set_auth_handler(auth)
		# perms = "read" # set the required permissions
		# url = auth.get_authorization_url(perms)
		# print url
		# print flickr.reflection.getMethodInfo(method_name = "flickr.photos.search")

		difftime = datetime.strptime(self.end_date, format_time) - datetime.strptime(self.start_date, format_time)
		intervals = difftime.days/365 #the difference by years
		year = timedelta(days=365)

		for i in range(0, intervals):
			min_taken_date = str(datetime.strptime(self.start_date, format_time) + year*i)
			max_taken_date = str(datetime.strptime(self.start_date, format_time) + year*(i+1))
			print "Collection start time is " + min_taken_date + "Collection end time is " + max_taken_date
			area_code = 1
			for area in self.bboxlist:
				print "Area " + str(area_code) +" is being searched now." 
				bboxpara = ','.join(str(v) for v in area)
				parameter = {"bbox":bboxpara,
							 "accuracy":self.accuracy,
							 "content_type":self.content_type,
							 "per_page":self.per_page,
							 "page": self.page,
							 "min_taken_date":min_taken_date,
							 "max_taken_date":max_taken_date
							}
				photoIDs = self.getPhotos(parameter)
				try:
					for photoID in photoIDs:
						photoInfo = self.getInfo(photoID)
						# print photoInfo
						self.savetomysql(self.table, photoInfo)
				except:
					Exception
					print "photo: " + str(photoID) + " is not acquired."  
				area_code += 1	


flickr_downloader = flickrDataCollection()
flickr_downloader.main()
# print flickr_downloader.getInfo('23536223114')
```
代码写的一般，有问题请大家在下方留言。

