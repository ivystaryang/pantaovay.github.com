---
comments: true
date: 2012-06-21 11:28:00
layout: post
slug: atoi_string_to_int
title: atoi（string到int）
wordpress_id: 114
categories:
- 编程
tags:
- 字符型转换
---







# atoi




<cstdlib>




int atoi ( const char * str );







Convert string to integer




Parses the C string _str_ interpreting its content as an integral number, which is returned as an int value.  

  

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial
_plus_ or _minus_ sign followed by as many numerical digits as possible, and interprets them as a numerical value.  

  

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.  

  

If the first sequence of non-whitespace characters in _str_ is not a valid integral number, or if no such sequence exists because either
_str_ is empty or it contains only whitespace characters, no conversion is performed.  






### Parameters




str
    C string beginning with the representation of an integral number.






### Return Value




On success, the function returns the converted integral number as an int value.  

If no valid conversion could be performed, a zero value is returned.  

If the correct value is out of the range of representable values, INT_MAX or INT_MIN is returned.  






### Example


`/* atoi example */   

#include <stdio.h>   

#include <stdlib.h>   

int main ()  

{   

int i;   

char szInput [256];  

printf ("Enter a number: ");   

fgets ( szInput, 256, stdin );  

i = atoi (szInput);   

printf ("The value entered is %d. The double is %d.n",i,i*2);   

return 0;   

}`


Output:


Enter a number: 73 The value entered is 73. The double is 146.  

  

那我们应该怎么用呢？看下面这个例子:  

比如我们要从文件中读取345+234；并且进行计算，没有空格。  

可能我们会想到用内核格式化，在+号，这种方法是可行的，但是如果式子换成345*234，就悲剧了。。  

所以我们必须采用逐字符的读法，然后将数字字符组合成int。  

string temp;//temp用来保存数字字符   

getline(in_file, infix);  

for(int i = 0; i < (int) infix.size(); i++)  

{  

if(isalnum(infix[j]))//如果是数字字符，需要cctype头文件   

{  

temp += infix[j];//追加到temp   

}  

else  

{  

cout << atoi(temp) << endl;//遇到其他非数字字符时说明读取结束，转换输出
  

}  

}  

当然了，这只是我的一种方法，相信大家有更好的方法。


  


