---
layout: post
title: "octopress中常用的标记语法"
date: 2012-11-24 22:42
comments: true
categories: octopress
---

这里记录下octopress的图片，视频，代码的引用的方式,

    {% img [class names] /path/to/image [width] [height] [title text [alt text]] %}

class names 可以填left或者right 图片的地址是以为source为/ ，所以source/img/a.png 应该
写成/img/a.png 不过不推荐把图片丢到代码库中，一般建议丢到有cdn的图床上，比如又拍云，
或者sae之类的地方，然后

    {%img http://1.sinapp.com/1.png 某图片 浮动显示 %}

就这么简单

添加代码的方式比较多
Code Block 的方式

    {% codeblock title lang:language url link text %}
    {% endcodeblock %}

囧，不想写了，贴官网的URL

http://octopress.org/docs/plugins/include-code/

http://octopress.org/docs/plugins/backtick-codeblock/

http://octopress.org/docs/plugins/gist-tag/

video的

http://octopress.org/docs/plugins/video-tag/
