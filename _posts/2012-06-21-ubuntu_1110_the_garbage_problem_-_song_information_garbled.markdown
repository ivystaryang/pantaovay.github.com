---
comments: true
date: 2012-06-21 11:32:00
layout: post
slug: ubuntu_1110_the_garbage_problem_-_song_information_garbled
title: ubuntu(11.10)的若干乱码问题--歌曲信息乱码
wordpress_id: 9
categories:
- linux
- OS
tags:
- ubuntu
- 乱码
---







原因同上篇日志，编码不同，所以需要转码；




直接上命令：




先安装mutagen：sudo apt-get install python-mutagen




然后转到你的MP3目录，例如我的歌曲放在系统的音乐文件夹则输入：cd /home/pantao（此为我的用户名，你需要换成你的用户名）/音乐




执行以全命令进行转换：mid3iconv -e GBK *.mp3






