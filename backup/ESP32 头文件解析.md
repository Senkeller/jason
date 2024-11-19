# 1、<> 以及“”的用法
`#include`
#include叫做文件包含命令，用来引入对应的头文件（.h文件）。
#include 也是C语言预处理命令的一种。

**#include语句的两种语法**
#include 的处理过程很简单，就是将头文件的内容插入到该命令所在的位置，从而把头文件和当前源文件连接成一个源文件，这与复制粘贴的效果相同。

> stdio.h 和 stdlib.h 都是标准头文件，它们存放于系统路径下，所以使用尖括号和双引号都能够成功引入。
> **_而我们自己编写的头文件，一般存放于当前项目的路径下，所以不能使用尖括号，只能使用双引号。_**

我们常看见的头文件是这样的：
`#include<stdio.h>`
**#include语句有两种方式包含头文件，分别是使用双引号" "与左右尖括号< >。**
其区别是（对于不是使用完全文件路径名的）头文件的搜索顺序不同：

**使用双引号" "的头文件的搜索顺序：**

- 1.包含该#include语句的源文件所在目录；
- 2.包含该#include语句的已经打开的头文件的逆序（因为头文件可以#include另一个头文件构成一个序列）；
- 3.编译选项-I所指定的目录
- 4.环境变量INCLUDE所定义的目录

就是：编译器首先在当前目录下查找头文件，如果没有找到，再到系统路径下查找。

使用左右尖括号< >的头文件的搜索顺序：
- 1.编译选项-I所指定的目录
- 2.环境变量INCLUDE所定义的目录

就是：编译器会到系统路径下查找头文件

也就是说，****使用双引号比使用尖括号多了一个查找路径，它的功能更为强大**。**

```
#include "stdio.h"
#include "stdlib.h"
```
同一个头文件可以被多次引入，多次引入的效果和一次引入的效果相同.
```
#include<stdio.h> 
#include<stdio.h> 
#include<stdio.h> 
#include<stdio.h> 
```

```
int main()
{
	int a=1;
	printf("%d\n",a);
	
	return 0;
}
```
运行文件包含允许嵌套，也就是说在一个被包含的文件中又可以包含另一个文件。
# 2、常用的头文件
```
#include <assert.h>    //设定插入点
#include <ctype.h>     //字符处理
#include <errno.h>     //定义错误码
#include <float.h>     //浮点数处理
#include <fstream.h>    //文件输入／输出
#include <iomanip.h>    //参数化输入／输出
#include <iostream.h>   //数据流输入／输出
#include <limits.h>    //定义各种数据类型最值常量
#include <locale.h>    //定义本地化函数
#include <math.h>     //定义数学函数
#include <stdio.h>     //定义输入／输出函数
#include <stdlib.h>    //定义杂项函数及内存分配函数
#include <string.h>    //字符串处理
#include <strstrea.h>   //基于数组的输入／输出
#include <time.h>     //定义关于时间的函数
#include <wchar.h>     //宽字符处理及输入／输出
#include <wctype.h>    //宽字符分类
```
# 3、头文件 stdio.h标（标准输入输出）
stdio 就是指 “standard input & output"（标准输入输出）
所以，源代码中如用到标准输入输出函数时，就要包含这个头文件！
例如c语言中的printf("%d",i); scanf("%d",&i);等函数。
引用方法
`#include <stdio.h>`
标准函数
```
int getchar()//从标准输入设备写入一个字符
int putchar()//向标准输出设备读出一个字符
int scanf(char*format[,argument…])//从标准输入设备读入格式化后的数据
int printf(char*format[,argument…])//向标准输出设备输出格式化字符串
char* gets(char*string)//从标准输入设备读入一个字符串
int puts(char*string)//向标准输出设备输出一个字符串
int sprintf(char*string,char*format[,…])//把格式化的数据写入某个字符串缓冲区
```
输入输出函数:该分类用于处理包括文件、控制台等各种输入输出设备，各种函数以“流”的方式实现
  ```
删除文件 remove
  修改文件名称 rename
  生成临时文件名称 tmpfile
  得到临时文件路径 tmpnam
  文件访问 关闭文件 fclose
  刷新缓冲区 fflush
  打开文件 fopen
  将已存在的流指针和新文件连接 freopen
  设置磁盘缓冲区 setbuf
  设置磁盘缓冲区 setvbuf

  格式化输入与输出函数 
  格式输出 fprintf
  格式输入 fscanf
  格式输出(控制台) printf
  格式输入(控制台) scanf
  格式输出到缓冲区 sprintf
  从缓冲区中按格式输入 sscanf
  格式化输出 vfprintf
  格式化输出 vprintf
  格式化输出 vsprintf

  字符输入输出函数 
  输入一个字符 fgetc
  字符串输入 fgets
  字符输出 fputc
  字符串输出 fputs
  字符输入(控制台) getc
  字符输入(控制台) getchar
  字符串输入(控制台) gets
  字符输出(控制台) putc
  字符输出(控制台) putchar
  字符串输出(控制台) puts
  字符输出到流的头部 ungetc

  直接输入输出 
  直接流读操作 fread
  直接流写操作 fwrite

  文件定位函数 
  得到文件位置 fgetpos
  文件位置移动 fseek
  文件位置设置 fsetpos
  得到文件位置 ftell
  文件位置复零位 remind

  错误处理函数 
  错误清除 clearerr
  文件结尾判断 feof
  文件错误检测 ferror
  得到错误提示字符串 perror
```
# 4、头文件 math.h（数学函数库）
数学函数库，一些数学计算的公式的具体实现是放在math.h里
引用方法
#include <math.h>

```
  反余弦 acos
  反正弦 asin
  反正切 atan
  反正切2 atan2
  余弦 cos
  正弦 sin
  正切 tan

  双曲余弦 cosh
  双曲正弦 sinh
  双曲正切 tanh

  指数函数 exp
  指数分解函数 frexp
  乘积指数函数 fdexp
  自然对数 log
  以10为底的对数 log10
  浮点数分解函数 modf

  ***幂函数 pow***
  平方根函数 sqrt

  ***求下限接近整数 ceil***
  绝对值 fabs
  求上限接近整数 floor
  求余数 fmod

```
# 5、头文件 string.h(字符串处理)
C语言里面关于字符数组的函数定义的头文件，常用函数有strlen、strcmp、strcpy等等，更详细的可以到include文件夹里面查看该文件。
引用方法
`#include <string.h>`
```
//常用函数如下：
strlen求字符串长度
strcmp比较2个字符串是否一样
strcat字符串连接操作
strcpy字符串拷贝操作
strncat字符串连接操作(前n个字符)
strncpy字符串拷贝操作(前n个字符)
strchr查询字串
strstr 查询子串
```
# 6、#是啥意思？
`#include<stdio.h>`
C语言中带#号的指令并不是C关键字的一部分,不属于C语言。

带#号的指令是写给编译器看的,告诉它一些事情,好让它更好的为C代码服务。

比如#include 指令就是告诉编译器看到这句话就要把我写的文件包含进来，#define指令就是告诉编译器看到这个宏就用前面已经定义好的内容替换。

咦？
问题又来了，有些同学又要问了#include这是啥头文件？
一个#来带的疑问啊，他们都是在程序最前边啊！

咱们在看一下==“百度百科”==中的“头文件”：

在C语言家族程序中，头文件被大量使用。一般而言，每个C++/C程序通常由头文件和定义文件组成。头文件作为一种包含功能函数、数据接口声明的载体文件，主要用于保存程序的声明，而定义文件用于保存程序的实现。
这个就是定义文件 define，宏定义，C语言中预处理命令一种。
分为无参宏定义和带参宏定义。

- 无参宏定义的一般形式为：#define 宏名 字符串；
- 带参宏定义的一般形式为：#define 宏名（参数表） 字符串。
