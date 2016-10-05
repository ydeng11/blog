---
title: 使用Selunium爬取微博数据
date: 2016-08-23 13:50:35
tags:
- Python
- Spider
categories: 编程
---

>其实移动端用requests可能更方便

## 平台和工具
最近想要分析下微博数据，在网上逛了几个小时后决定爬取移动端的微博数据。这样做的好处是移动端数据爬取方便，但同时数据量也会偏小。做初步分析的话，应该还是足够的，如果想要全部的数据，最好还是从网页端爬取。
如题所示，使用的爬取工具是selenium，具体的安装和用法大家可以去[官网](http://selenium-python.readthedocs.io/installation.html)查询。<!-- more -->

## 获取Cookies
虽然是在移动端爬取数据，但是验证码还是绕不过去的。这里有两个解决办法，第一个是将验证码截图然后使用OCR技术进行识别和输入，第二个是暂停逻辑，由人工来代替机器输入验证码。使用第二个办法时，我们可以将网站的cookies存储在本地方便以后使用。

```python
Cookies.py
```

```python
# -*- coding: utf-8 -*-
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import pickle
import time
import sys
reload(sys)
sys.setdefaultencoding('utf8')

class saveCookies():
    def __init__(self):
        print "开始获取cookies"
        self.username = "your weibo name"
        self.password = "your weibo password"

    def getCookies(self):

        driver = webdriver.Chrome()
        driver.get('http://login.weibo.cn/login/')
        driver.delete_all_cookies()
        if driver.find_element_by_name('mobile'):
            driver.find_element_by_name('mobile').send_keys(self.username)
            driver.find_element_by_xpath("//input[@type='password']").send_keys(self.password)
            if driver.find_element_by_name("code"):
                while True:
                    val = driver.find_element_by_name("code")
                    # print val.get_attribute("value")
                    time.sleep(5)
                    if val and len(val.get_attribute("value"))>0:
                        code = val.get_attribute("value")
                        val.clear()
                        driver.find_element_by_name("code").send_keys(code)
                        break
                    pass
                pass
            driver.find_element_by_name('submit').click()
            print '成功登录'
        
        wait = WebDriverWait(driver, 10)
        element = wait.until(EC.presence_of_element_located((By.NAME,'smblog')))
        if element:
            pickle.dump(driver.get_cookies() , open("cookies.pkl","wb"))
            print "The cookies is saved."
            driver.close()

# test = saveCookies()
# test.getCookies()
# test = getCookies("weibo_username","weibo_password")
```

## 使用Cookies登录并爬取数据
我在这里爬取的微博数据主要与输入的关键词相关, 以腾冲为例， 网页端大概有70w条左右，但是移动端只能显示出100页，每页大概有10-20条。这么小的数据量，我暂时就将数据存储到文本文档，之后爬取网页端数据的时候还是选择存储到数据库。关于数据分析的方面，等过几天把中文的自然语言处理分析学习下再写一下。

```python
saveWeibo.py
```

```python
# -*- coding: utf-8 -*-
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
import pickle
import time
import sys
import re
reload(sys)
sys.setdefaultencoding('utf8')


class saveWeibo():
    def __init__(self):
        self.keyword = u""

    def getWeibo(self):
        infofile = open("SinaWeibo1.txt", 'wb')
        driver = webdriver.Chrome()
        driver.get('http://login.weibo.cn/login/')
        cookies = pickle.load(open("cookies.pkl", "rb"))
        for cookie in cookies:
            driver.add_cookie(cookie)
        driver.get('http://weibo.cn')
        keyword = self.keyword
        # input_text = driver.find_element_by_name("keyword")
        # input_text.send_keys(keyword)
        # submit = driver.find_element_by_name('smblog') 
        # submit.click()
        # comment = driver.find_elements_by_xpath("//a[@class='cc']")
        # content = driver.find_elements_by_xpath("//div[@class='c']")
        # all_comment_url = []               #存储所有文件URL
        # i = 0
        # j = 0
        # infofile.write(u'开始:\r\n')
        # print u'长度', len(content)
        # while i<len(content):
        #     #print content[i].text
        #     if (u'收藏' in content[i].text) and (u'评论' in content[i].text): #过滤其他标签
        #         print content[i].text
        #         infofile.write(u'微博信息:\r\n')
        #         infofile.write(content[i].text + '\r\n')
        #         div_id = content[i].get_attribute("id")
        #         print div_id
        #         while(1):  #存在其他包含class=cc 如“原文评论”
        #             url_com = comment[j].get_attribute("href")
        #             if ('comment' in url_com) and ('uid' in url_com):
        #                 print url_com
        #                 infofile.write(u'评论信息:\r\n')
        #                 infofile.write(url_com+'\r\n')
        #                 all_comment_url.append(url_com)    #保存到变量里
        #                 j = j + 1
        #                 break
        #             else:
        #                 j = j + 1
                    
        #     i = i + 1
        # nextPage = driver.find_element_by_link_text(u"下页")
        # nextPage.click()
        # infofile.close()
        print '\n'  
        print u'获取微博内容信息'  
        num = 1  
        while num <= 100:  
            url_wb = "http://weibo.cn"+ "/search/mblog?hideSearchFrame=&keyword=%E8%85%BE%E5%86%B2&page=" + str(num)  
            print url_wb  
            driver.get(url_wb)  
            #info = driver.find_element_by_xpath("//div[@id='M_DiKNB0gSk']/")  
            info = driver.find_elements_by_xpath("//div[@class='c']")
            # for value in info:
            #     if u'赞' not in value.text:
            #         continue
            #     else:
            #         print value.text
            #         print "-------------------------"

            for value in info:  
                # print value.text
                # print "-----------"
                # info = value.text  
  
                #跳过最后一行数据为class=c  
                #Error:  'NoneType' object has no attribute 'groups'  
                if u'赞' not in value.text:
                    print u'跳过', value.text, '\n' 
                    continue                    
                else:  
                    if (u'转发了') not in value.text:
                        print u'原创微博'  
                        infofile.write(u'原创微博\r\n')  
                    else:  
                        print u'转发微博'  
                        infofile.write(u'转发微博\r\n')  
                          
                    #获取最后一个点赞数 因为转发是后有个点赞数
                    print value.text
                    str1 = value.text.split(u" 赞")[-1]
                    print str1
                    print "``````````````````"
                    if str1:   
                        val1 = re.match(r'.*?(\d+)', str1, re.S).groups(1)
                        print u'点赞数: ', val1  
                        infofile.write(u'点赞数: ' + str(val1) + '\r\n')  
  
                    str2 = value.text.split(u" 转发")[-1]  
                    if str2:   
                        val2 = re.match(r'.*?(\d+)', str2, re.S).groups(1)
                        print u'转发数: ', val2  
                        infofile.write(u'转发数: ' + str(val2) + '\r\n')  
  
                    str3 = value.text.split(u" 评论")[-1]  
                    if str3:  
                        val3 = re.match(r'.*?(\d+)', str3, re.S).groups(1)
                        print u'评论数: ', val3  
                        infofile.write(u'评论数: ' + str(val3) + '\r\n')  
  
                    str4 = value.text.split(u" 收藏 ")[-1]  
                    flag = str4.find(u"来自")  
                    print u'时间: ' + str4[:flag]  
                    infofile.write(u'时间: ' + str4[:flag] + '\r\n')  
  
                    print u'微博内容:'  
                    print value.text[:value.text.rindex(u" 赞")]  #后去最后一个赞位置  
                    infofile.write(value.text[:value.text.rindex(u" 赞")] + '\r\n')  
                    infofile.write('\r\n')  
                    print '\n'  
            else:  
                print u'next page...\n'  
                infofile.write('\r\n\r\n')  
            num += 1  
            print '\n\n'  
        print '**********************************************'  

    def main(self):
        self.getWeibo()

    # def getweibo(self):

test = saveWeibo()
test.main()
```
>感谢[Eastmount的专栏](http://blog.csdn.net/eastmount/article/details/50720436)
>感谢[静觅的专栏](http://cuiqingcai.com/2599.html)