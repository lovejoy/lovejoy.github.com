---
layout: post
title: "更新 octopress"
date: 2014-08-30 15:28:25 +0800
comments: true
categories: 
---

如何更新octopress
```
git remote add octopress https://github.com/imathis/octopress.git
git pull octopress master     # Get the latest Octopress
bundle update                # Keep gems updated #我试了用bundle install 结果说Bundler could not find compatible versions for gem "sass"
rake update_source            # update the template's source
rake update_style             # update the template's style
```
对于在新机器上运行
```
curl -L https://get.rvm.io | bash -s stable --ruby
cd some_dir && rvm install 提示你安装的
bundle install
```
日常注意保存
```
git push　＃提交octopress相关改动
git push origin source　#提交博客内容改动
```
