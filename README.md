爬虫练习
========

场景
----
由于最近学习Python, 缺少练习的项目, 又一直对Python的爬虫闻名已久, 所以就做了这个基于拉勾网数据的爬虫练习.

爬虫目标
--------
主要爬取拉勾网在深圳的PHP职位信息.

爬虫组成
--------
爬虫主要由三部分组成: 
1. 爬取代理ip程序
2. 爬取拉勾网在深圳的PHP职位信息程序
3. 使用sqlite3保存爬取回来的职位信息

(PS: 爬虫主要使用`bs4`和`requests`这两个库完成)

遇到的问题
----------
主要的问题是拉勾网的反爬虫机制.

遇到的反爬虫策略有:
- 接口User-agent做了判别
- 接口请求referer做了辨认
- 每个ip的访问频率做了限制
- 每个ip的访问量做了限制

解决办法
--------
- 对于User-agent, 简单点, 就是模拟浏览器, 这个是最基本, 一般网站都会有的反爬虫. 因为Python 爬虫中的User-agent 不做模拟的话, 输出直接是python的.
- 对于职位接口做的referer辨认, 是本身接口后台接口加的一个辨认, 直接在拉勾网, 用`F12`查看后台接口(Ajax请求)即可知道.
- 对于访问频率, 尽可能慢点, 同人差不多是最好的.
- 对于访问量, 则需要代理ip了. 网上有很多免费代理ip, 可以去爬取使用, 不过一般都是不稳定, 失效性很高.

如何使用本项目
--------------
本项目的系统环境: `Arch Linux` + `Python 3.5.2` + `sqlite3`.  
在`venv`下运行, 并且安装了`requests`, `bs4`库.

直接在命令窗口下运行: 
```
(venv)$ python Lagou.py   #()表示在venv环境
```
另外需要说明的是:   
项目中的`proxy.txt`是在国外的一个免费代理站爬取的,  
由于使用`requests`库无法访问国外的站点(不知道如何使用翻墙, 本人的翻墙基于ss sock5),   

为了省事, 直接用浏览器翻墙把免费代理站的几个页面保存为html文件放在`htmls`文件下,  
再使用`Proxy.py`脚本解释获取`proxy ip`存放在`proxy.txt`文件中, 供`Lagou.py`脚本使用.

(PS: 由于国内的许多免费代理失败率实在是太高了, 所以找国外的, 但每次要获取新代理都要去手动保存一次html文件, 心好累...)

待完善
------
- 多线程爬取职位信息
- 把代理ip做成服务接口

结语
----
通过本项目, 充分练习了一次Python爬虫.  
基本上一些常见的反爬虫策略都遇上了, 对爬虫以及Python这门语言都有了深刻的认识.  

另外, 对Python越发的衷爱了.  
简单, 即是美.  