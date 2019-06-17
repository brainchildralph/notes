1.

memchr檢測的是一段內存，strchr檢測的是一個字符串 如果一段內存中有0x0的話，顯然不能用strchr去查找的。建議看看兩個函數的原型


2.

strchr會停在\0，memchr不會，看接口就明白了：

NAME
       memchr, memrchr - scan memory for a character

SYNOPSIS
       #include <string.h>
       void *memchr(const void *s, int c, size_t n);
       void *memrchr(const void *s, int c, size_t n);

NAME
       strchr, strrchr - locate character in string

SYNOPSIS
       #include <string.h>
       char *strchr(const char *s, int c);
       char *strrchr(const char *s, int c);


3.

mem*系針對字節
str*系針對字符
2個概念


4.

mem  的效率高


5.

類似strcpy memcpy


6.

memchar針對與內存操作，shtchr只能是字符串操作
--------------------- 
作者：bat67 
来源：CSDN 
原文：https://blog.csdn.net/bat67/article/details/52063132 
版权声明：本文为博主原创文章，转载请附上博文链接！
