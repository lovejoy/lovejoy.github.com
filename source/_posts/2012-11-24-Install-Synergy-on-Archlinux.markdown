---
layout: post
title: "Install synergy on Archlinux"
date: 2012-11-24 15:12
comments: true
categories: archlinux
---

synergy 是一个很好的多平台的共享鼠标键盘的开源工具，极大的满足了我在linux,mac,windows 上的对键盘
和鼠标共享的需求。其早期的版本在linux和mac上是没有图形化界面的，但是到最新的1.4.10已经有了很好的
统一的图形化界面了,但是我在archlinux的官方仓库中安装的这个版本却还是没有界面的，与此同时官方提供
的rpm和deb的安装包却是有界面的。虽然archlinux的aur中也有第三方的图形化的配置工具如quicksynergy和
qsynegy ,但是我试了下quicksynergy 后表示其界面真是弱的惨不忍睹.无奈只能手动配置了，记录如下

    section: screens
        linux-t0sv:
                halfDuplexCapsLock = false
                halfDuplexNumLock = false
                halfDuplexScrollLock = false
                xtestIsXineramaUnaware = false
                switchCorners = none 
                switchCornerSize = 0
        chakra-pc:
                halfDuplexCapsLock = false
                halfDuplexNumLock = false
                halfDuplexScrollLock = false
                xtestIsXineramaUnaware = false
                switchCorners = none 
                switchCornerSize = 0
    end

    section: aliases
    end

    section: links
            linux-t0sv:
                    down = chakra-pc
            chakra-pc:
                    up = linux-t0sv
    end
    
    section: options
            relativeMouseMoves = false
            screenSaverSync = true
            win32KeepForeground = false
            switchCorners = none 
            switchCornerSize = 0
    end

只要改一下上面的2个机器名成自己的就ok了，然后丢到~/.synergy.conf
然后用synergys -f 启动，可以看到比较详细的信息，或者rc.d start synergys 
作为服务的方式启动，当然也可以设置成开机启动，在/etc/rc.conf 的DAEMONS=
(...synergy...) 加入就行了
