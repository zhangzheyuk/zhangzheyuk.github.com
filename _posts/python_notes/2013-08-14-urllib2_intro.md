---
layout: post
title: "urllib2 intro"
description: ""
category: python
tags: [python]
---
{% include JB/setup %}
<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. ulrlib2</a></li>
<li><a href="#sec-2">2. Basic use</a></li>
<li><a href="#sec-3">3. use the urllib to mirror a Request</a></li>
<li><a href="#sec-4">4. use the urllib to construct a POST request</a></li>
<li><a href="#sec-5">5. GET request</a></li>
<li><a href="#sec-6">6. Headers</a></li>
<li><a href="#sec-7">7. Error handling</a></li>
</ul>
</div>
</div>

# ulrlib2

based on the python manual "how to" part

# Basic use

try to get fetch the webpage

    import urllib2 
    response = urllib2.urlopen('http://python.org/')
    html = reponse.read() 

# use the urllib to mirror a Request

    import urllib2
    
    req =  urllib2.Request('http://www.voidspace.org.uk')
    response = urllib2.urlopen(req)
    the_page = response.read()

# use the urllib to construct a POST request

(can use this feature to do the auto authetication)

    import urllib
    import urllib2
    
    url = 'http://www/someserver.com/cgi-bin/register.cgi'
    value = {'name' : 'Led Chang'
    'location': 'QD'
    'language': 'Python'}
    
    data = urllib.urlencode(values)
    req = urllib2.Request(url, data)
    response = urllib2.urlopen(req)
    the_page = response.read()  

# GET request

GET request 明文传输数据

> get and post (转)
> 原理介绍：理论上说，GET是从服务器上请求数据，POST是发送数据到服务器。事实上，GET方法是把数据参数队列（query string）加到一个URL上，值和表单是一一对应的。比如说，name=John。在队列里，值和表单用一个&符号分开，空格用+号替换，特 殊的符号转换成十六进制的代码。因为这一队列在URL里边，这样队列的参数就能看得到，可以被记录下来，或更改。通常GET方法还限制字符的大小（大概是 256字节 ）。事实上POST方法可以没有时间限制的传递数据到服务器，用户在浏览器端是看不到这一过程的，所以POST方法比较适合用于发送一个保密的（比如信用 卡号）或者比较大量的数据到服务器。
> GET是把参数数据队列加到提交表单的ACTION属性所指的URL中，值和表单内各个字段一一对应，在URL中可以看到
> POST是通过HTTP POST机制，将表单内各个字段与其内容放置在HTML HEADER内一起传送到ACTION属性所指的URL地址。用户看不到这个过程。
> 对于GET方式，服务器端用Request.QueryString获取变量的值，
> 对于POST方式，服务器端用Request.Form获取提交的数据。
> 
> 区别：
> Post是允许传输大量数据的方法，而Get方法会将所要传输的数据附在网址后面，然后一起送达服务器，因此传送的数据量就会受到限制，但是执行效率却比Post方法好。 
> 
> 
> 建议：
> 1、get方式的安全性较Post方式要差些，包含机密信息的话，建议用Post数据提交方式；
> 2、在做数据查询时，建议用Get方式；而在做数据添加、修改或删除时，建议用Post方式；

    >>> import urllib
    >>> data={}
    >>> data['name'] = 'Somebody Here'
    >>> data['location'] = 'Northampton'
    >>> data['language'] = 'Python'
    >>> url_values = urllib.urlencode(data)
    >>> print url_values
    name=Somebody+Here&language=Python&location=Northampton
    >>> url = 'http://www.example.com/example.cgi'
    >>> full_url = url + '?' + url_values
    >>> data = urllib2.urlopen(full_url)

# Headers

add headers to the HTTP request
contains about the version of the OS and web browser

    import urllib
    import urllib2
    
    url = 'http://www.someserver.com/cgi-bin/register.cgi'
    user_agent = 'Mozilla/4.0 (compatible; MSIE 5.5; Windows NT)'
    values = {'name' : 'Michael Foord',
    'location' : 'Northampton',
    'language' : 'Python' }
    headers = { 'User-Agent' : user_agent }
    
    data = urllib.urlencode(values)
    req = urllib2.Request(url, data, headers)
    response = urllib2.urlopen(req)
    the_page = response.read()

# Error handling

