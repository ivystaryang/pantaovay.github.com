---
comments: true
date: 2012-08-14 14:19:15
layout: post
slug: mbrfix-%e5%88%a0%e9%99%a4linux%e7%b3%bb%e7%bb%9f
title: MbrFix 删除linux系统
wordpress_id: 173
categories:
- linux
- OS
- windows
tags:
- linux
- mbrfix
- win7
- 修复引导
---

硬盘安装ubuntu（其他linux没用过，应该也可以的）和win7双系统，如果想要删除linux系统，在win7下直接删除分区是万万不能的。如果你删除了，再次开机就无法引导。MbrFix就是解决这个问题的必备利器。
首先，下载MbrFix：[http://www.linuxidc.com/linux/2007-11/8785.htm
](http://www.linuxidc.com/linux/2007-11/8785.htm)
第二，将MbrFix解压到C盘根目录。cmd进入命令行，切换到C盘根目录下（cd命令），输入命令：MbrFix /drive 0 fixmbr，确定。然后，就可以将linux的分区删除。

如果，已经到了不能进入系统的地步也没关系，用安装光盘启动系统，进入命令行界面，输入fixmbr就好；用pe的话使用相应的引导修复工具也可以。

总之，这不是什么大问题，遇到这种情况完全没必要重装系统。![](http://www.pantaothu.cn/wp-includes/images/smilies/icon_twisted.gif)
