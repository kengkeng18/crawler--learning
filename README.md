# crawler--learning

python学习慕课：https://www.icourse163.org/course/BIT-1001870001

requests库：第三方网络爬虫库
Cancel changes
robots.txt 网络爬虫排除标准

## requests库入门
www.python-requests.org

![image](https://user-images.githubusercontent.com/45223160/141294890-b06e41fd-06d0-4658-b25b-d80df8d48727.png)

### requsets方法
有七个，一般最常用的是get和head
```
r=requests.get(url,params=None,kwargs)
```

![image](https://user-images.githubusercontent.com/45223160/141295527-38655123-44d6-475f-aaab-4c18f62a651b.png)

r.encoding:从http head中猜测的响应内容编码方式，如果head中不存在charset，则默认编码为ISO-8859-1   
r.apparent_encoding:根据网页内容分析出编码方式

#### 爬取网页的通用代码框架
```  
def getHTMLText(url)
  try:
     r=requests.get(url,timeout=30)
     r.raise_for_status() #如果状态不是200，引发HTTPError异常
     r.encoding = r.apparent_encoding
     return r.text
  except:
     retuen "产生异常"
```    
#### http协议
url格式 http://host[:port][path]   
port:可省略，默认80   

get:请求获取url位置的资源   
head：请求获取url位置资源的头部信息   
post：向url位置的资源后附加新的数据   
put：向url位置存储一个资源，覆盖原url位置的资源   
patch；局部更新url位置的资源   
delete：删除url位置存储的资源   

#### requests方法
requests.request(method,url,kwargs)   
kwargs 13个控制访问参数，均为可选项   
params:字典或   
data   
json   
headers   
cookies   
auth   
files   
timeout   
proxies   
allow_redirects   
stream   
verify   
cert   
