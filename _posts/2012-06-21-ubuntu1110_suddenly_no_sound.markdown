---
comments: true
date: 2012-06-21 11:31:00
layout: post
slug: ubuntu1110_suddenly_no_sound
title: ubuntu11.10突然没有声音
wordpress_id: 7
categories:
- linux
- OS
tags:
- ubuntu
---







Y460 ubuntu11.10 x64




今天想看 bing bang的时候竟然没有声音，以前是有声音的，在这里绝对应该不是驱动的问题。




试了下banshee，也是没声音。




于是拜求谷歌，终于找到解决办法，重启alsa就可以了。




具体操作：sudo /sbin/alsa force-reload (第一次使用reload，没成功，看来还是的强制重新加载啊)






