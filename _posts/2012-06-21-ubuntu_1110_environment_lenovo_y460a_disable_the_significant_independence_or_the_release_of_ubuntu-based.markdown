---
comments: true
date: 2012-06-21 11:35:00
layout: post
slug: ubuntu_1110_environment_lenovo_y460a_disable_the_significant_independence_or_the_release_of_ubuntu-based
title: Ubuntu 11.10环境 联想Y460A禁用独显(或者基于ubuntu的发行版)
wordpress_id: 120
categories:
- linux
- OS
tags:
- linux
- ubuntu
---



联想Y460A笔记本，以前用 Ubuntu 10.04 LTS 版本，就用此方法禁用独显，现更新到 Ubuntu 11.10，图形桌面也从GNOME更换到了Unity。

此方法仍然可用。

1： 终端中输入  sudo apt-get install git

安装acpi_call 模块

2：  下载此文件
**免费下载地址在** [http://linux.linuxidc.com/](http://rrurl.cn/gSg24O)

**用户名与密码都是**www.linuxidc.com

**具体下载目录在** /pub/2011/10/21/Ubuntu 1110环境 联想Y460A禁用独显/

3： 解压文件到某文件夹下，比如  /home/x/system

4： 如下图，依次键入如下命令，最后若成功提示如黄色框内，且笔记本左下侧面的独显指示灯熄灭即成功

cd  acpi_call

make

sudo insmod acpi_call.ko

./test_off.sh

5.  开机即自动禁用独显

终端键入如下命令：

sudo gedit /etc/rc.local

在打开的文档中添加如下内容  （路径根据具体情况修改）

insmod  /home/x/system/acpi_call/acpi_call.ko

sh /home/x/system/acpi_call/test_off.sh

即可开机自动禁用独显

查看显卡：

www.linuxidc.com@linuxidc:~$lspci |grep VGA

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

01:00.0 VGA compatible controller: ATI Technologies Inc Madison [AMD Radeon HD 5000M Series] (rev ff)



原文地址：http://www.linuxidc.com/Linux/2011-10/45725.htm


