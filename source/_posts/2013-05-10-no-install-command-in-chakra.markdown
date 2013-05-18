---
layout: post
title: "chakra或者arch中没有/bin/install的问题"
date: 2013-05-10 10:25
comments: true
categories: linux chakra
---

刚在chakra中装meraspolit 提示 make: /bin/install：命令未找到 不知道arch中有没有这个问题
这个install 命令没有就搞笑了。这个是coreutils中的东西怎么可能没有？which install 了一下，
好嘛在/usr/bin/install 中ruby装东西的时候掉的是/bin/install 就不能直接调install吗,
建个软链接过去 sudo ln -s /usr/bin/install /bin/install 再用ccr装的时候就搞定了
