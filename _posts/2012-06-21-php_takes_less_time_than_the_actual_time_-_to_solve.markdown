---
comments: true
date: 2012-06-21 11:29:00
layout: post
slug: php_takes_less_time_than_the_actual_time_-_to_solve
title: PHP获取时间比实际时间少--解决
wordpress_id: 116
categories:
- 编程
---




调用date()函数




--------------------------------------------------------------------------------------------------------------------




有两方法   

  

1、我们写PHP程序在获取时间时，人为加上(这种方法是最实用也是最土的方法)   

  

2、如果直接获取正确时间，也可修改PHP的配置文件，即查找php.ini文件 修改方法：在php.ini文件中找到下面这行： ;date.timezone = 将上面这行的;注释符去掉，后面加上PRC（中国人民共和国的英文单词缩写），即改成下面这样： date.timezone = PRC 如果php.ini文件中没有上面这行，直接加上就行了




从php5.10开始，php中加入了时区的设置，在php中显示的时间都是格林威治标准时间，这就造成了我们中国的用户会差八个小时的问题！  

相关设置是修改php.ini中的 date.timezone 参数：  

[Date]  

; Defines the default timezone used by the date functions  

;date.timezone =




默认是关闭的，只需把注释去掉，改为即可  

[Date]  

; Defines the default timezone used by the date functions  

date.timezone = PRC




其中PRC是“中华人民共和国”！  

其他选项可以参考php手册。  

不过这上面的亚洲地区漏掉了我们的首都北京，不知道老外是不是故意的！




如果没有修改php.ini的权限，只需要在调用时间日期函数的时候，调用 date_default_timezone_set(’PRC’) 即可！  

也可以调用date_default_timezone_get()来查看当前的时区设置！




關於XXX，大陸內地可用的值是：  

Asia/Chongqing ，Asia/Shanghai ，Asia/Urumqi （依次為重慶，上海，烏魯木齊)  

港台地區可用：Asia/Macao ，Asia/Hong_Kong ，Asia/Taipei （依次為澳門，香港，台北）  

台灣地区可設為：date.timezone = "Asia//Taipei"  

還有新加坡：Asia/Singapore




  

安装好php5后，在论坛不经意间，在论坛上看到有人说php5.1.2的时间显示整整少8个小时，  

<?php  

echo date("Y-m-d H:i:s");  

?>  

结果自己测试果然是相差8小时。  

  

后来经过在论坛上找资料，结果终于解决，在php5以及起以上的版本，要输出本地的时间（限中国），可以这么写代码：  

<?php  

date_default_timezone_set('Asia/Shanghai');   

echo date('Y-m-d H:i:s');  

?>




也可以这样写代码:  

<?php  

date_default_timezone_set('Asia/Chongqing');   

echo date('Y-m-d H:i:s');  

?>  

  

这样 时间相差八小时的问题就解决了!!~~~




--------------------------------------------------------------------------------------------------------------------




至于为什么只有上海和重庆，却没有北京，我也不是太清楚



