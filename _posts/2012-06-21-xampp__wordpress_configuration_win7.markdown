---
comments: true
date: 2012-06-21 11:35:00
layout: post
slug: xampp__wordpress_configuration_win7
title: xampp+wordpress配置(win7)
wordpress_id: 119
categories:
- OS
- windows
tags:
- apache
- php
- web
- win7
---




首先到xampp官网下载xampp，貌似没有x64的，直接安装，这里我选的d盘，安装完之后会有一个XAMPP Control Panel，启动之后在界面里很容易进入各个地方的；




其次，进入主页之后选择 安全 设置相应用户名和密码；




然后，进入Mysql，新建一个数据库，命名为wordpress（随意），设置权限以及密码！




最后，是配置wordpress，同样下载wordpress，这里是一个解压包，将解压出来的wordpress文件夹拷贝到xampp的安装路径下的htdocs文件夹里，打开，wp-config（后面有个什么东西）.php这个文件用记事本打开（注意需要改名为wp-config.php），




// ** MySQL 设置 - 具体信息来自您正在使用的主机 ** //




/** WordPress 数据库的名称 */  

define('DB_NAME', '和你设置的名字一样');  

  

/** MySQL 数据库用户名 */  

define('DB_USER', '你设置的用户名');  

  

/** MySQL 数据库密码 */  

define('DB_PASSWORD', '你设置的密码');




然后ctrl+s保存就好了；（注意命名的问题wp-config.php）




下面，打开浏览器，在地址栏输入http(s)://localhost/wordpress/wp-admin/index.php（加s是加密的貌似）,即可！进入你的数据库之旅吧！




ps:linux平台下比较简单！






