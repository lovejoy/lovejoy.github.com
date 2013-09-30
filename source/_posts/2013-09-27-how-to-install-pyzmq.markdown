---
layout: post
title: "手动安装pyzmq记录"
date: 2013-09-27 10:27
comments: true
categories: 
---
##Zeromq是什么
Zeromq是一个简单好用的传输层，像框架一样的一个 socket library,也是一个消息处理队列库,

但是它并不是像rabbitmq一样是传统意义上的消息队列，而更像是一个现代化的网络通讯编程的接口。

##如何安装zeromq
zeromq 比较简单，直接编译安装就好了
```
wget http://download.zeromq.org/zeromq-3.2.4.tar.gz
./configure CC=$JUMBO_ROOT/opt/gcc46/gcc --prefix=$JUMBO_ROOT
make
make install
```

##如何安装pyzmq

默认情况下可以直接pip install pyzmq

但是出了bundled/zeromq/src/ip.cpp: In function `zmq::fd_t zmq::open_socket(int, int, int)':

bundled/zeromq/src/ip.cpp:45: error: `SOCK_CLOEXEC' was not declared in this scope

error: command 'gcc' failed with exit status 1`'的错误

所以想办法直接从源码安装
```
git clone https://github.com/zeromq/pyzmq.git

pip install cython #dev版需要用cython`

python setup.py config --cc=JUMBO_ROOT/opt/gcc46/bin/gcc

python setup.py  configure --zmq=$JUMBO_ROOT

python setup.py install 

```
