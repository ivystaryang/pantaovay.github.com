---
comments: true
date: 2012-07-16 19:02:00
layout: post
slug: ipv6_tunnel_configuration_test_passes_t
title: IPV6隧道配置 (T大测试通过)
wordpress_id: 24
categories:
- linux
- OS
- windows
tags:
- 善用佳软
---

**什么是IPV6?**

IPV6是继IPV4的下一代IP协议。目前，全球网络采用TCP/IP协议。IP是TCP/IP协议族中网络层的协议，是TCP/IP协议族的核心协议。大家所熟悉的IPV4地址已经接近枯竭（？），IPv4中规定IP地址长度为32，最大地址个数为2的32次方；而IPv6中IP地址的长度为128，即最大地址个数为2的128次方。与32位地址空间相比，其地址空间增加了2^128-2^32个。所以IPV6地址就数量上来讲，基本可以实现其使地球上的每一粒沙子都拥有一个IP地址的宣言。另外，现在高速发展的物联网，没有IPV6的支持，根本无从谈起。


**什么是ISATAP隧道?**

ISATAP（ draft-ietf-ngtrans-ISATAP-23.txt）的全名是 Intra-Site Automatic Tunnel Addressing Protocol，它将IPv4地址夹入IPv6地址中，当两台 ISATAP 主机通讯时，可自动抽取出 IPv4 地址建立 Tunnel 即可通讯，且并不需透过其它特殊网络设备，只要彼此间IPv4网络通畅即可。

**清华ISATAP隧道相关地址**



	
  * 清华大学 ISATAP隧道路由器的IPv4地址是：isatap.tsinghua.edu.cn

	
  * 用户设置 ISATAP隧道的接入点为：isatap.tsinghua.edu.cn

	
  * 清华大学 ISATAP 隧道IPv6地址前缀为: 2402:f000:1:1501::/64


**配置方法（win7）**

打开控制台窗口**cmd**



	
  1. C:>netsh

	
  2. C:>int

	
  3. C:>ipv6

	
  4. C:>isatap

	
  5. C:>set router isatap.tsinghua.edu.cn

	
  6. C:>set state enabled


这样隧道就设置好了，不过还没有结束，需要更改网络适配器的设置：**取消IPv6协议**

[![取消ipv6](http://pantaothu2-wordpress.stor.sinaapp.com/uploads/2012/07/取消ipv6-150x150.png)](http://pantaothu2-wordpress.stor.sinaapp.com/uploads/2012/07/取消ipv6.png)
可以到http://ipv6.tsinghua.edu.cn测试是否正在使用ipv6。

**修改HOSTS文件（你懂的）**

有一个不定时更新的源：[http://code.google.com/p/ipv6-hosts/](http://code.google.com/p/ipv6-hosts/)
