---
title: 使用Requests时报告“InsecurePlatformwarning”
date: 2016-08-23 23:56:59
tags: 
- Python
- Spider
- Requests
categories: 系统
---

> 还是该用scrapy吧。

在调用requests中post或get命令时，常常会有报错”InsecurePlatFormingWarning”出现，虽然并不影响程序运行，但还是很不爽啊。在网上搜索了一下办法，<!---more--->首先是要确定requests是更新到最新版了，否则需要安装一个额外的包。
```
pip install 'requests[security]'
```

另外一个简单的办法就是直接无视，强行关闭warning。
```
import requests.packages.urllib3
requests.packages.urllib3.disable_warnings()
```
