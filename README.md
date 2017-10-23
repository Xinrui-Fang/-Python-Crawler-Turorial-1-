# -Python-Crawler-Turorial-1  
## 爬虫思路 
我们打开一个网页，即是通过了HTTP协议，对一个资源进行了请求，如何他返还你一份 HTML文档，然后浏览器进行文档的渲染。所以，我们只需要模拟浏览器，发送一份请求，获得这份文档，再抽取出我们需要的内容就好</br>

## 简单爬虫
**`import urllib`   
`response=urllib.urlopen("http://www.baidu.com")`   
`print response.read()`**   
* 首先，我们引入python的urllib库  
* 然后，我们对一个url地址进行反问</br>
* 我们就可以看到，一版面的 HTML代码了，就是这么简单，使用python
## 进阶1

### 伪装 User-Agent
`import urllib2`

`header={`</br>
    `"User-Agent":"Mozilla/5.0 (Macintosh; Intel Mac OS X 10.11; rv:43.0) Gecko/20100101 Firefox/43.0",`</br>
    `"Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8",`</br>
    `"Host":"aljun.me"`</br>
`}`</br>
`request=urllib2.request("http://xxx.com",header=header)`</br>
`response=urllib2.urlopen(request)`</br>

### cookie发送
`import urllib2`</br>
`import cookielib`</br>

`cookie={"bdshare_firstime":1455378744638}`</br>
`cookie = cookielib.CookieJar()`</br>

`opener = urllib2.build_opener(urllib2.HTTPCookieProcessor())`</br>

`urllib2.install_opener(opener)`</br>

`response=urllib2.urlopen("http://xxx.com")`</br>

### 数据交互
`import urllib2`

`data={`</br>
    `"username":"xxx"`</br>
   ` "password":"xxx"`</br>
`}`</br>
`request=urllib2.request("http://xxx.com",data)`</br>
`response=urllib2.urlopen(request)`</br>

## 爬取图片
`import urllib`

`path="xxx.png"`</br>
`url="http://zhaduixueshe.com/static/pic/discovery.png"`

`urllib.urlretrieve(url,path)`</br>
* 官方推荐做法，非常快，而且好用  
* [Request](http://www.python-requests.org/en/master/user/quickstart/)库链接  

## 正则表达式re
`import urllib2`</br>
`import re`

`reg=r'http.(d+).jpg'`</br>
`reg=re.compile(reg)`</br>
`response=urllib2.urlopen("http://xxx.com")`</br>
`result=re.findall(response.read(),reg)`</br>
* 用来匹配文档  
## beautifulsoap 
`from bs4 import BeautifulSoup`</br>
`soup = BeautifulSoup(html_doc, 'html.parser')`

`print(soup.prettify())`

`###`</br>
`<html>`</br>
   ` <head>`</br>
      `  <title>首页</title>`</br>
   ` </head>`</br>
   ` <body>`</br>
    `    <h1>我是标题</h1>`</br>
     `   <img src="xxx">`</br>
    `</body>`</br>
`</html>`

`soup.title`</br>
`# <title>The Dormouse's story</title>`</br>

`soup.title.name`</br>
`# u'title'`

`soup.title.string`</br>
`# u'The Dormouse's story'`

`soup.title.parent.name`</br>
`# u'head'`

`soup.p`</br>
`# <p class="title"><b>The Dormouse's story</b></p>`

`soup.p['class']`</br>
`# u'title'`

`soup.a`</br>
`# <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>`

`soup.find_all('a')</br>
`# [<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,`</br>
`#  <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,`</br>
`#  <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]`

`soup.find(id="link3")`</br>
`# <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>`

* 用来编译HTML代码的专业库

## pyquery
[pyquery](http://aljun.me/post/17)库链接 
* pyquery是以jquery的选择器语法为基础，非常适合前端转来的

## 调用json格式
`In [1]: import urllib2`

`In [2]: response=urllib2.urlopen("http://aljun.me/like")`

`In [3]: print response.read()`</br>
`{`</br>
  `"liked": 1647`</br>
`}`</br>
