# -Python-Crawler-Turorial-1-   
## 爬虫思路 
我们打开一个网页，即是通过了HTTP协议，对一个资源进行了请求，如何他返还你一份 HTML文档，然后浏览器进行文档的渲染。所以，我们只需要模拟浏览器，发送一份请求，获得这份文档，再抽取出我们需要的内容就好</br>
## 简单爬虫
**`import urllib`   
`response=urllib.urlopen("http://www.baidu.com")`   
`print response.read()`**   
* 首先，我们引入python的urllib库  
* 然后，我们对一个url地址进行反问</br>
* 我们就可以看到，一版面的 HTML代码了，就是这么简单，使用python
