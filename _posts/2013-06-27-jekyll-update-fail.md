---
layout: post
title: "jekyll本地调试成功，github没更新"
description: ""
category: jekyll
tags: [notes]
---
{% include JB/setup %}
* 今天Update了一下blog，访问的时候发现总是没有更新，就觉得非常奇怪，我还以为是github的问题，

因为在我本地测试的时候是正常的，但是push上去之后发现网页没有什么变化.查看github page的help,试一

试加上.nojekyll然后在.gitignore里取消掉_site.不用github来编译。结果发现没有什么用.  

* 最后偶然试一试旁边同事的电脑，发现他访问果没有问题，我就很疑惑，以为Firefox的缓存问题，结果

清理完缓存之后，发现还是不行，下楼找别人访问，结果发现居然跟我一样是错误的结果，我就纳闷了。忽然

想到可能是我们用的proxy有问题，它把网页放到cache里了，于是我用手机访问，果然没问题。坑爹的代理.
