---
layout: post
title: "download the picture by auto"
description: ""
category: python
tags: [python]
---
{% include JB/setup %}


<div id="content">
<h1 class="title">download the picture by auto</h1>
<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. Intro</a></li>
<li><a href="#sec-2">2. Code</a></li>
</ul>
</div>
</div>

<div id="outline-container-sec-1" class="outline-2">
<h2 id="sec-1"><span class="section-number-2">1</span> Intro</h2>
<div class="outline-text-2" id="text-1">
<p>
简单介绍一下，最近比较忙，一些文章Notes在evernote里，没时间整理写blog,毕竟
是从note的三言两语整理出Blog还是需要时间的，而且也不是cnblog那种直接就可以
粘贴发布的。
这个是前一段无聊写的一个从内部bbs相亲版块爬图片的小程序，用来练习。很简单的说明
了爬图片的基本远离：
找到开始爬的网址，制定规则，拿到图片的url，然后下载，值得注意的是我这边用的都是
最简单的，以后如果可以完善的方向有以下：
</p>
<ol class="org-ol">
<li>可以添加多线程
</li>
<li>可以改进未必只是拿到clear的网址，有些网站是用AJAX,但是我觉得也是可以模拟请
求，以前看过某大牛说过，web前端是没有安全性可言的。
</li>
<li>关于拿到html之后，进行清洗，我使用的是最简单的正则，其实有比较professional
的模块,beautiful soap之类的。
</li>
</ol>
</div>
</div>
<div id="outline-container-sec-2" class="outline-2">
<h2 id="sec-2"><span class="section-number-2">2</span> Code</h2>
<div class="outline-text-2" id="text-2">
<div class="org-src-container">

<pre class="src src-python"><span style="color: #ff7f24;">#!/usr/bin/env python</span>
<span style="color: #ff7f24;"># -*- coding:utf-8 -*-</span>
<span style="color: #ff7f24;"># used for the clear url address</span>

<span style="color: #00ffff;">import</span> urllib
<span style="color: #00ffff;">import</span> urllib2
<span style="color: #00ffff;">import</span> os
<span style="color: #00ffff;">import</span> re
<span style="color: #00ffff;">import</span> sys
<span style="color: #00ffff;">from</span> threading <span style="color: #00ffff;">import</span> Thread
<span style="color: #00ffff;">import</span> time
<span style="color: #00ffff;">import</span> random
<span style="color: #00ffff;">import</span> hashlib

<span style="color: #ff7f24;">#&#33719;&#21462;html</span>
<span style="color: #00ffff;">def</span> <span style="color: #87cefa;">gethtml</span>(url):
    page = urllib2.urlopen(url)
    html = page.read()
    <span style="color: #00ffff;">return</span> html

<span style="color: #ff7f24;">#&#33719;&#21462;&#22270;&#29255;URL</span>
<span style="color: #00ffff;">def</span> <span style="color: #87cefa;">getImg</span>(html):
    reg = r<span style="color: #ffa07a;">'file="(attachments/.*?.jpg)"'</span>
    imgre = re.compile(reg)
    imglist = re.findall(imgre,html)
    <span style="color: #00ffff;">print</span> <span style="color: #ffa07a;">"imglist:"</span>,imglist 
    <span style="color: #00ffff;">return</span> imglist

<span style="color: #ff7f24;">#&#19979;&#36733;&#25991;&#20214;&#65292;&#20445;&#23384;&#25991;&#20214;</span>
<span style="color: #00ffff;">def</span> <span style="color: #87cefa;">downloadFile</span>(urllist):
    x = 0
    filepath = <span style="color: #ffa07a;">"f:\Pythontest1"</span>
    <span style="color: #ff7f24;"># if os.path.exists(filepath) is True:</span>
    <span style="color: #ff7f24;">#     filepath += "1"</span>

    <span style="color: #ff7f24;"># os.mkdir(filepath)</span>

    <span style="color: #00ffff;">for</span> imgurl <span style="color: #00ffff;">in</span> urllist:
        temppath = filepath + <span style="color: #ffa07a;">"\%s.jpg"</span> %x
        urllib.urlretrieve(<span style="color: #ffa07a;">"http://websvr03.qd.lucent.com/"</span> + imgurl,temppath)
        x += 1

<span style="color: #00ffff;">if</span> <span style="color: #b0c4de;">__name__</span> == <span style="color: #ffa07a;">"__main__"</span>:

    html = gethtml(<span style="color: #ffa07a;">"http://websvr03.qd.lucent.com/viewthread.php?tid=23737&amp;extra=page%3D1"</span>)
    <span style="color: #00ffff;">print</span> html

    <span style="color: #00ffff;">print</span> r<span style="color: #ffa07a;">"-----------------&gt;&gt;&#33719;&#21462;HTML&#23436;&#27605;"</span>.decode(<span style="color: #ffa07a;">"utf-8"</span>).encode(<span style="color: #ffa07a;">"gbk"</span>)  <span style="color: #ff7f24;">#&#35299;&#20915;CMD&#25511;&#21046;&#21488;&#19978;&#20013;&#25991;&#20081;&#30721;&#30340;&#38382;&#39064;  </span>
    urllist =  getImg(html)  
    <span style="color: #00ffff;">print</span> r<span style="color: #ffa07a;">"------------------&gt;&gt;&#20998;&#26512;URL&#23436;&#27605;"</span>.decode(<span style="color: #ffa07a;">"utf-8"</span>).encode(<span style="color: #ffa07a;">"gbk"</span>)  
    downloadFile(urllist)  
    <span style="color: #00ffff;">print</span> r<span style="color: #ffa07a;">"-------------------&gt;&gt;&#25991;&#20214;&#19979;&#36733;&#23436;&#27605;"</span>.decode(<span style="color: #ffa07a;">"utf-8"</span>).encode(<span style="color: #ffa07a;">"gbk"</span>)
</pre>
</div>
</div>
</div>
</div>
<div id="postamble" class="status">
<p class="author">Author: zhang led</p>
<p class="date">Created: 2013-09-15 Sun 17:47</p>
<p class="creator"><a href="http://www.gnu.org/software/emacs/">Emacs</a> 23.4.1 (<a href="http://orgmode.org">Org</a> mode 8.0.7)</p>
<p class="xhtml-validation"><a href="http://validator.w3.org/check?uri=referer">Validate XHTML 1.0</a></p>
</div>

