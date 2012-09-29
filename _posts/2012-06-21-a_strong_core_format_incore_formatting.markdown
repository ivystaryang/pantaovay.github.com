---
comments: true
date: 2012-06-21 11:28:00
layout: post
slug: a_strong_core_format_incore_formatting
title: 强大的内核格式化（incore formatting）
wordpress_id: 115
categories:
- 编程
tags:
- 内核格式化
---



#include <iostream>  

#include <string>  

#include <sstream>  

using namespace std;  

int main()  

{  

string lit = "378+123;";  

  

istringstream instr(lit);  

int word;  

while(instr >> word)  

cout << word << endl;  

return 0;  

}  

结果当然是 378 123啦  


