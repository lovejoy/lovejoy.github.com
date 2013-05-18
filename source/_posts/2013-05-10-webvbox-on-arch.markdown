---
layout: post
title: "在arch上使用webvbox"
date: 2013-05-10 10:48
comments: true
categories: archlinux linux
---
http://webvbox.com/ 是一个不错的linux网络视频播放器 默认提供了deb的按照包，tar.gz 的包也提供了，不过是放在115上的囧

已经down下来，在终端中./install.sh 安装，装完点图标一闪而过，什么也没有。。。。

丢到终端中运行，显示error while loading shared libraries: libhunspell-1.2.so.0: cannot open shared object file: No such file or directory
尝试安装libhunspell 发现没有，然后自然的就想到了搜索hunspell还真有这个东西，装上，运行还是这个问题。看了下/usr/lib 中的有这个，不过是版本1.3的，
而软件要1.2 的，所以sudo ln -s libhunspell-1.3.so.0 libhunspell-1.2.so.0 轻松搞定 再运行还是有问题
/webvbox: error while loading shared libraries: libstartup-notification-1.so.0: cannot open shared object file: No such file or directory
这下就聪明了直接安装 pacman -S startup-notification 搞定，终于能用了，囧。。。qiyi貌似对vdpau有问题。。。
