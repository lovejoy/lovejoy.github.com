---
layout: post
title: "Mail的乱码问题"
date: 2013-05-10 11:07
comments: true
categories: mac
---

Mail是Mac上的官方邮件客户端

Mail 的乱码问题是由于发送的邮件是mime格式，outlook/express 等无法正确识别。
由于mail的默认编码是 utf8，而 outlook 的默认编码是gb2312/gbk，如果 mail 回复邮件则会使用 utf8，
而当 html 的 charset 和实际编码有出入在 IE 中会无法正确识别。这就是为什么同样用 webmail，在 firefox 下显示正常，而 IE 则乱码。
虽说是 IE 的问题，但是还是可以解决这个问题的，方法有3:

* 使用纯文本方式（ mail 格式里选择制作纯文本）
* 在新建邮件或者回复 outlook 类发送的邮件，手工指定编码（在 mail 的邮件－文本编码 选择 utf8 或者简体中文/GBK/GBK18030 等编码 ）
* 如果嫌每次如此操作太麻烦，可以修改 mail 的默认值，由于这个选项没有界面可选，我们需要用命令来执行或者直接修改 mail 的 plist 文件：

退出mail，在终端输入:
    defaults write com.apple.mail NSPreferredMailCharset "GBK"    （最好用这个，其它的各有各的问题）
或者：
    defaults write com.apple.mail NSPreferredMailCharset "UTF-8"
    defaults write com.apple.mail NSPreferredMailCharset "EUC"
    defaults write com.apple.mail NSPreferredMailCharset "GB18030" 再开启 Mail 收发邮件就正常了。
要还原的话，输入：
    defaults write com.apple.mail NSPreferredMailCharset "UTF-8"

>http://www.son1c.cn/show/1270.html
