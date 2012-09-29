---
comments: true
date: 2012-06-21 11:32:00
layout: post
slug: ubuntu_1110_the_garbage_problem_-_the_gedit_garbled
title: ubuntu(11.10)的若干乱码问题--gedit乱码
wordpress_id: 10
categories:
- OS
- windows
tags:
- ubuntu
- 乱码
---







**ubuntu11.10**更新了太多的东西，原来在10.04下的方法已经不适用了（gconf-editor直接没有了）google之，找到一个不错的解决方法：






  * 首先在终端中执行： sudo apt-get install dconf-tools（这是替换gconf-editor的家伙）
  * 然后输入dconf-editor
  * 找到org—>gnome—>gedit—>preferences—>encodings—>auto-detected
  * 在最前面添加 ‘GB18030′,’GB2312′,’GBK’,输入完后敲回车键才能保存输入的内容。  

  





我的文件修改后是：['UTF-8','GB18030','GB2312','GBK','BIG5','CURRENT','UTF-16']。然后ubuntu11.10就能顺利的显示txt中文再也不会出现**中文乱码了**。







乱码原因，一般都是编码不同的问题： Windows下的txt用的是GBK编码，而getdit默认用的是UTF-8编码，所以会出现乱码。







另一中，命令行解决方案：gsettings set org.gnome.gedit.preferences.encodings auto-detected "['UTF-8','GB18030','GB2312','GBK','BIG5','CURRENT','UTF-16']"，即可






