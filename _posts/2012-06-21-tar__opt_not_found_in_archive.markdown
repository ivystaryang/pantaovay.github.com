---
comments: true
date: 2012-06-21 11:34:00
layout: post
slug: tar__opt_not_found_in_archive
title: 'tar: /opt：归档中找不到'
wordpress_id: 118
categories:
- linux
- OS
tags:
- linux
---







处理方法是在后面加上-C参数




比如，之前如果用# tar zxvf lumaqq_2006M2-linux_gtk2_x86_no_jre.tar.gz /opt/ 的话就会出现这个问题




但是用# tar zxvf lumaqq_2006M2-linux_gtk2_x86_no_jre.tar.gz ** -C** /opt/ 就可以了




需要root权限






