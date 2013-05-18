---
layout: post
title: "在raspberry pi上使用transmission"
date: 2013-05-18 20:07
comments: true
categories: rpi
---
先安装transmission-daemon
    sudo apt-get install transmission-daemon

默认会自己启动，为了改配置文件，需要先手动关闭服务

    sudo service transmission-daemon stop

然后更改在/etc/transmission-daemon/ 下的配置文件settings.json

{% gist 5604224 %}

有几个地方需要改，下载目录download-dir改为你自己的下载目录,port-forwarding-enabled改为true,这个
是控制upnp的，开了端口才能有用（找了半天才找到这个问题，默认居然是关闭的），还有rpc-username，rpc-password
自己看着改一下，是登录web界面的用户名密码，另外rpc-whitelist-enabled改为false，不然外网无法访问web界面
另外在树莓派上使用外接硬盘或者U盘，作为下载目录的，碰到Permission denied 的时候，需要改下transmission的启动脚本

    sudo vim /etc/init.d/transmission-daemon
    把
    USER=debian-transmission
    改为
    USER=root

这也是个坑爹的地方，transmission原来的下载目录是/var/lib/transmission-daemon 这下面的目录的用户是debian-transmission的
(搞不懂干嘛弄个专门给transmission用的用户),但是又不方便在外挂硬盘上chown改变目录的用户权限，改不了，还有能改的话，别的软件又会出问题。

<!-- more -->

到这里可以启动了

    sudo service transmission-daemon start

另外发现一个很不错的transmission的web界面

    wget https://transmission-control.googlecode.com/files/tr-control-easy-install.sh
    sudo ./tr-control-easy-install.sh

{% img http://bcs.duapp.com/picstore/Hn4xH27fu5.png 800 400 transmission-control %}
