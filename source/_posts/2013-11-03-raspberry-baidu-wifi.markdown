---
layout: post
title: "raspberry-baidu-wifi"
date: 2013-11-03 20:04
comments: true
categories: 
---
sudo rpi-update
git clone --depth 1 https://github.com/raspberrypi/linux.git
sudo ln -s linux /lib/modules/3.6.11+/build
make mrproper
gzip -dc /proc/config.gz > .config
make oldconfig
make prepare
make modules_prepare
wget https://github.com/raspberrypi/firmware/raw/master/extra/Module.symvers
make
sudo make install 
You can stop this by editing the os/linux/rt_linux.c

Change the line
ULONG RTDebugLevel = RT_DEBUG_TRACE;
to
ULONG RTDebugLevel = RT_DEBUG_ERROR;
allow-hotplug ra0
iface ra0 inet dhcp
    wpa-ssid meow
        wpa-psk "miaolegemide7752942&"
        #wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
