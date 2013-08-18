---
layout: post
title: "在raspberry上使用mldonkey同时解决移动磁盘权限的问题"
date: 2013-05-19 00:18
comments: true
categories: rpi
---

在树莓派上用mldonkey本来应该是一件很简单的事情，但是用上外挂硬盘之后，就各种蛋疼的问题了。
首先安装
```
sudo apt-get install mldonkey
```
安装完成之后修改配置文件
```
sudo vim /var/lib/mldonkey/downloads.ini
修改allowed_ips为0.0.0.0/0
然后自己看情况修改下载目录
shared_directories
```
正常这样访问raspberry pi 的4080端口就可以看到mldonkey的web界面，可以使用了。
但是我的移动硬盘的分区是fat32格式的，mldonkey就没有权限写文件了，这点可以通过
```
ps -ef |grep mlnet
sudo cat /etc/passwd
```
看出来,有一个uid为109,名为mldonkey的用户,然后mldonkey会以这个用户启动，WTF

照着之前处理transmission时的经验，尝试将mldonkey的进程以root用户执行，仔细读一下/etc/init.d/mldonkey-server同时观察/var/log/mldonkey/mlnet.log的日志就可以发现，用户的指定在
/etc/default/mldonkey-server文件
所以更改下mldonkey的启动账户
```
sudo vim /etc/default/mldonkey
将原来的3个字段改成下面这样
MLDONKEY_DIR=/root/.mldonkey
MLDONKEY_USER=root
MLDONKEY_GROUP=root
```
然后把默认的配置文件移动到root帐号的home目录下
```
sudo cp -r /var/lib/mldonkey /root/.mldonkey/
```
这样就可以正常使用啦
```
sudo service mldonkey-server restart
```
如果你不需要外挂磁盘的话就不需要这样玩

