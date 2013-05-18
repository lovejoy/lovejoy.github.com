---
layout: post
title: "BT5R2汉化，装中文语言包"
date: 2013-05-10 09:51
comments: true
categories: linux
---

Gentoo 被ko了，所以打算用bt5做主力系统，bt5装完是没有中文的，虽然可以显示中文。
首先去mirrors.163.com下载一下源地址列表，下载10.04的，因为bt5r2是基于10.04.03的
http://mirrors.163.com/.help/sources.list.lucid

在终端中输入
    gedit  /etc/apt/source.list 
同时双击打开从163下载的，把163的复制进系统里面的，注意不要覆盖原有的。
    apt-get install language-support-zh language-pack-zh
    apt-get install language-selector
然后正常去切换成中文就行了
