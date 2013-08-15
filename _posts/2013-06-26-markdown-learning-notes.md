---
layout: post
title: "Markdown learning notes"
description: ""
category: Markdown
tags: [notes]
---
### Markdown常用语法

Based on [this](http://www.ituring.com.cn/article/23)

####- 链接:     
    

    main[words](link)

####- code引用: 行首空出四个space 
  

    pubilic class blog(){
    char* owner;
    }

####- 字体类型: 
 
    
    *斜体* **粗体**

 *斜体*   **粗体**
 
####- 段内换行：行尾加两个空格


    这里打算段内换行+space+space  

这里打算换行  
这是下一行的开始

####- 引用


    >引来一段话"Beauty is our bussiness."

>"Beauty is our bussiness."

####- 图像的使用


    
    ![图片](http://img.hb.aicdn.com/c817b7909a0481b5b029b47f88df52cec9e8c2a65b7f-S4JrY8_fw580)


![图片](http://img.hb.aicdn.com/c817b7909a0481b5b029b47f88df52cec9e8c2a65b7f-S4JrY8_fw580)
还是需要首先上传到图床上去呀，以为跟orgmode一样可以内联。


 
###关于category 和 tags的设置:

   1. category: 后面的空格不能省。。。开始我写成了category:sth.死活都不出

   2. tags: 一定要加\[\],即使是单个tag也必须加。。


###在先编辑markdown文件很好的网站

[http://mahua.jser.me/](http://mahua.jser.me/)


###Emacs下的Markdown mode

[http://linuxtoy.org/archives/emacs-markdown-mode.html](http://linuxtoy.org/archives/emacs-markdown-mode.html) 

{% include JB/setup %}
