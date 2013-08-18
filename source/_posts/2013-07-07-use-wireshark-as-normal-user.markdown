---
layout: post
title: "以普通用户运行wireshark"
date: 2013-07-07 12:13
comments: true
categories: linux
---

wireshark通过/usr/bin/dumpcap 来抓取数据包，这个文件的权限如下
```
-rwxr-xr-- 1 root wireshark 84524 22.06.2013 23:56 /usr/bin/dumpcap
```
所以只需要将自己加入wireshark用户组就可以了

```
sudo gpasswd -a username wireshark
sudo usermod -a -G wireshark username
```
以上二选一即可，之后
```
getcap /usr/bin/dumpcap
```
输出的结果是cap_net_admin,cap_net_raw+eip 但是我的却不是，又查了下
```
setcap cap_net_raw,cap_net_admin=eip /usr/bin/dumpcap 
```
手动设置一下，再开启wireshark就OK了
