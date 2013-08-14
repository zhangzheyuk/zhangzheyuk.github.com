---
layout: post
title: "orgmode html jekyll各种折腾"
description: ""
category: jekyll 
tags: [jekyll]
---
{% include JB/setup %}
<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#sec-1">1. 关于配置Jekyll的html post</a></li>
</ul>
</div>
</div>
# 关于配置Jekyll的html

-   记录下来今天的折腾，我的需求本来是希望jekyll能支持html的显示，
    这样的话，我每次写blog的时候就只需要用org然后export生成html
    就OK了，虽然makedown的语法也是很方便，但是毕竟还是用org的比较
    习惯。

-   查了jekyll的官方document，没有确切的说明直接可以在<sub>post里解</sub>
    析，看了orgmode的网站上有一篇是直接使用org写jekyll，但是悲剧
    的是我用的是JB在jekyll上的二次封装，本身我对web也不是很熟悉，
    估计会花很大的effort,这就跟我的目的不一样了，不是我学习的重点

-   最后在orgmode的manul里发现了最新版本的org支持从org file exprot
    出.md文件。兴高彩烈的安了最新版本的orgmode，结果C-c, C-e之后
    发现emacs报错了。。definition is void: org-defvaralias"
    回头排查init.el的时候发现之前加过一个O-blog的插件，把load删除
    掉之后终于可以用了。下一步就是定制org-export出的md文件前面把
    title加上就ok了。

-   最后我在publish的时候发现了一个非常关键的问题，我一直执着与要
    在post里放入html文件。其实只需要把org导出的html的body部分copy
    出来放在md文件里就OK了。。。还可以很完美的使用css的效果。

