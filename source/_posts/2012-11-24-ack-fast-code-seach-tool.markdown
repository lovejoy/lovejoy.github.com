---
layout: post
title: "Ack更加快速的代码搜索工具"
date: 2012-11-24 21:56
comments: true
categories: tool
---

通常我们搜代码是这么玩的

    grep -R xxx .

速度慢不说，返回的结果还没有高亮,而ack的返回结果是这样的:

{% img http://bcs.duapp.com/picstore/GitbGsLhsc.png %}

既有高亮还有行号,ack其实是一个perl的脚本，代码如下

各linux发行版应该都有这个软件包了，自行安装就行了，
代码有5000多行，不想看的请勿点击阅读全文

<!-- more -->

{%gist 4139833 %}
