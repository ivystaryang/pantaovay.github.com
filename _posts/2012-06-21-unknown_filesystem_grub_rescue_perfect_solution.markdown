---
comments: true
date: 2012-06-21 11:39:00
layout: post
slug: unknown_filesystem_grub_rescue_perfect_solution
title: unknown filesystem grub rescue 完美解决
wordpress_id: 125
categories:
- linux
- OS
tags:
- linux
- ubuntu
---




昨天晚上在win7下重新分了一下盘，虽然没有动linux的磁盘分区，但是整个的磁盘分区表毕竟是变了。今天开机就发生这么杯具的事，着实让我出了一把汗，经过多不探索（谷歌强大啊，百度真的sb），终于完美解决！




首先，说一下出现这种状况的原因：我在windows下用分区工具重新进行了分区（虽然没有动Linux所在分区）




注：双斜杠//之后的内容为命令解释，无需输入




解决方法：




第一步：找出你的Linux盘在那个分区以及grub目录在什么位置。




如果你还记得最好，忘了也无所谓，使用下面命令逐个试探即可。




grub rescue>ls 回车 //列出本机所有磁盘及分区，比如:（hd0）,(hd0,msdos1)




//,(hd0,msdos4),(hd0,msdos7),(hd0,msdos8),(hd0,msdos9)等




循环使用如下命令，直至显示该分区所包含内容而不是“unknown filesystem




grub rescue>ls (hd0,msdosX)/boot/grub 回车




假设我们试到(hd0,msdos9)时，成功显示了内容。




第二步：




grub rescue>set root=(hd0,msdos9) 回车 //括号里为上一步尝试成功的分区




grub rescue>set prefix=(hd0,msdos9)/boot/grub 回车




第三步：




grub rescue>insmod /boot/grub/normal.mod 回车




至此，应该退出了grub rescue模式，进入了熟悉的grub模式(表现是字体的颜色变了，此时可以送一口气了)




第四步：




grub>normal 回车




第五步：修复grub




进入Linux系统后，在命令行里




sudo update-grub 回车




第六步：




sudo grub-install /dev/sda //sda是你的启动磁盘




修复成功就会提示Installation finished. No error reported!




ok了！！






