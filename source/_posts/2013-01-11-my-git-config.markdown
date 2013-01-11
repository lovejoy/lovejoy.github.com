---
layout: post
title: "我的一些git配置以及平时碰到的git相关问题"
date: 2013-01-11 16:20
comments: true
categories: git
---
我的~/.gitconfig文件
{% gist 4508928 %}
直接写配置文件就好了，命令党自重:-)
实现的功能：
    git difftool 可以直接调用meld来显示diff
    git diff 还是原来的那个，不过把默认把语法高亮加上了
    git st 表示git status的意思，少敲几个字母

一些日常遇到的git的问题

merge相关
    git merge lovejoy 最正常的merge lovejoy分支
    git merge lovejoy hash数字 merge lovejoy分支该hash的那一次commit
    git merge --abort 后悔了，回到merge前的状态
diff相关
    我的配置中difftool很好的解决了diff2个分支的情况
    git difftool lovejoy master
    git difftool lovejoy master xxx.php 只看一个文件

meld 需要安装pygtksourceview2来显示语法高亮,在设置中自行开启
