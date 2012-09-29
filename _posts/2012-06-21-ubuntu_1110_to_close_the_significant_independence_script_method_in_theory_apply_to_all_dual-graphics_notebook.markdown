---
comments: true
date: 2012-06-21 11:32:00
layout: post
slug: ubuntu_1110_to_close_the_significant_independence_script_method_in_theory_apply_to_all_dual-graphics_notebook
title: ubuntu(11.10)关闭独显（脚本法，理论上适用所有双显卡笔记本）
wordpress_id: 8
categories:
- linux
- OS
tags:
- linux
- ubuntu
---



**实测在Ubuntu 11.10上可以正常工作。**

我的笔记本是联想小y，有集成的i卡，还有独立的ATI HD5600系列，但是在运行Ubuntu的时候，因为没有什么需要独显的应用，就想到要关闭独显，只使用集显，省电又降温~不然声音很大，让人很不爽～～

使用其他笔记本的同学请自行测试可用性，也欢迎反馈~~

准备工作：安装了ATI闭源驱动的请先卸载，在BIOS里禁用了双显卡切换的请先开启
首先在终端下执行这条命令：

cat /sys/kernel/debug/vgaswitcheroo/switch

如果类似这样（主要是两个状态都是Pwr）：








12


`0:IGD:+:Pwr:0000:00:02.0``1:DIS: :Pwr:0000:01:00.0`




就说明你的两块显卡都开着，那么就按照下面的步骤做吧
建立一个脚本/usr/local/sbin/vgaswitcher








12

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26


`#!/bin/bash` 

`if` `[ ``"$(whoami)"` `!= ``"root"`
`]; ``then`

`   ``echo` `"Use as root"`

`   ``exit` `1`

`fi`



`if` `[ -z ``"$1"` `]; ``then`

`        ``cmd=``"OFF"`

`else`

`   ``if` `[ ``"$1"` `= `
`"-i"` `]; ``then`

`      ``cmd=``"DIGD"`

`   ``elif` `[ ``"$1"` `= `
`"-d"` `]; ``then`

`      ``cmd=``"DDIS"`

`   ``else`

`           ``cmd=$1`

`   ``fi`

`fi`



`if` `([ ``"$cmd"` `!= ``"OFF"`
`] && [ ``"$cmd"` `!= ``"DDIS"` `
] && [ ``"$cmd"` `!= ``"DIGD"` `]); `
`then`

`        ``echo` `"Bad Command!"`

`        ``exit` `1`

`fi`



`echo` `"$cmd"` `> ``/sys/kernel/debug/vgaswitcheroo/switch`

`cat` `/sys/kernel/debug/vgaswitcheroo/switch`




然后再建立一个启动脚本/etc/init.d/vgaswitch








12

3

4

5

6

7

8


`#!/bin/bash` 

`if` `[ ``"$1"` `!= ``"start"`
`]; ``then`

`   ``exit``;`

`fi`



`/usr/local/sbin/vgaswitcher`

`/usr/local/sbin/vgaswitcher` `-i`




都建立好以后，执行如下命令：








1


`sudo` `chmod` `+x ``/usr/local/sbin/vgaswitcher`
`/etc/init``.d``/vgaswitch` `&& ``sudo`
`update-rc.d vgaswitch defaults`




重启就可以禁用掉独显了~
可以再次执行最开始的命令来查看状态：








1


`cat` `/sys/kernel/debug/vgaswitcheroo/switch`




现在应该是这样了（一个Pwr，另一个Off）：








12


`0:IGD:+:Pwr:0000:00:02.0``1:DIS: :Off:0000:01:00.0`




这样就好了～～机器的温度一下子就降下来了～～另外在系统设置里也是集成显卡而不是之前的无法识别了，看来这就是shell编程的魅力啊～

这样就不妨碍大家使用ubuntu的心情了！





