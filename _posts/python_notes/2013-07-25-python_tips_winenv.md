---
layout: post
title: "Python tips"
description: ""
category: python
tags: [python, 图像搜索]
---
{% include JB/setup %}
#### Python win下编程的问题
在windows下想写个自动的脚本来玩玩，一旦在windows下果然各种各样的问题
纷纷搞出来了。


1. 首先是最关键的问题，How to run the python scripts,在linux下
   根本不会操心这个问题呀，which python,有了直接执行就OK，我先装了
   一个2.7的在windows下，然后把路径加到环境变量path里，自从大学学过
   java以后好久没改过环境变量了。执行的时候CMD cd到目录下，跟linux
   是一样的执行。
   需要注意的是windows下cmd，是直接敲D: + enter直接换盘符，好久没
   用，我还cd f:试了半天。。  


2.  中文编码格式的问题，我代码中注释加了几行中文，结果出来的

    error SyntaxError:    
    Non-ASCII character '\xc6' in file game.py on    
    line 9, but no encoding declared; 
    see http://www.python.org/peps/pep-0263.html for details  
     
解决办法：# -*- coding: UTF-8 -*-指定编码格式。
   
然后emacs又出问题了，我save的时候emacs报

    Warning (mule): Invalid coding system 'UTF-8' is specified 
    for the current buffer/file by the :coding tag. It is highly 
    recommended to fix it before writing to a file.
  
So, 改成# -*- coding: utf-8 -*-
妈妈再也不用担心我的学习了。。。

#### Python xrange 问题
     xrange
     函数说明：用法与range完全相同，所不同的是生成的不是一个数组，而是一个生成器。
     xrange更适合用作循环里

#### Python 逗号的问题
   在计算海明距离有几行code没有看的特别明白。

#### Python 图像处理相关
    1. 灰度以及PIL模块里的处理
    [Link](http://qinxuye.me/article/implement-sketch-and-pencil-with-pil/)
    2. 有关图像搜索，相似图形比对
    [阮一峰的Blog](http://www.ruanyifeng.com/blog/2011/07/principle_of_similar_image_search.html)
