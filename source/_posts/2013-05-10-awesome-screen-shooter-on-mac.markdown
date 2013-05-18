---
layout: post
title: "牛B哄哄的Mac截图"
date: 2013-05-10 10:50
comments: true
categories: mac
---
mac原生自带了截图的功能，而且是程序员喜爱的快捷键方式，不是win7上的那个傻逼方式
首先来说一下有两种方式

* 全屏截图Command＋shift＋3 屏幕回闪一下，然后截图会以屏幕快照xxxx的方式保存到桌面
* 区域截图Command＋shift＋4

关于区域截图
按Command＋shift＋4 后 ,画一个抓取的区域，不要松开鼠标，接着

* 按住空格可以移动这个区域
* 按住 Shift后，将锁定X 或者 Y轴进行拖动
* 按住 Option后 将按照区域圆心进行放大.

最后所有截图将直接显示在桌面上。
虽然没有窗口截图等更加复杂的功能，但是这些已经够用了不是吗

Tips

你可以以你喜欢的方式来改版mac截图的默认名称，只需在终端输入以下命令即可
    defaults write com.apple.screencapture name Screenshot
    killall SystemUIServer

如何弄掉阴影

    defaults write com.apple.screencapture disable-shadow -bool true
    killall SystemUIServer

恢复

    defaults write com.apple.screencapture disable-shadow -bool false
    killall SystemUIServer

想给mac的登陆界面截图，用这个

    /System/Library/CoreServices/loginwindow.app/Contents/MacOS/loginwindow

