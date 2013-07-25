---
layout: post
title: "linux安全相关"
description: ""
category: Security
tags: [Security]
---
{% include JB/setup %}

Based on [this](http://linux.chinaitlab.com/safe/826400.html)

#### BIOS安全
设置BIOS密码

#### LILO安全
编辑lilo.conf文件

#### 禁用相关帐号
* 删除用户帐号: userdel demo

* 删除群组号: groupdel demo

#### 选择适当密码

/etc/rsyslog.conf

/etc/login.defs

#### SUID/SGID

find / -perm -04000 -type f -ls
1. with suid and sgid, use 6000 to search
2. sgid , 2000
3. suid , 4000
