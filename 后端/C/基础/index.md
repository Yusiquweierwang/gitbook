
[toc]




## 常用操作

### 小命令
```c
g++ init.cpp&& ./a.out
//&&代表前一个命令编译成功就执行后一个命令。

```
![1684034649314](image/index/1684034649314.png)

### 进制转换


## basic
### 历史
早期：打孔带

二进制指令

汇编语言
10110000 01100001
对应
MOVE AL

应用：操作系统的底层代码


C:1973
C++ : 1979

难点：内存管理

java:自动申请内存。不用去申请内存，手动申请和手动释放。有自己的内存管理机制。

write once , run anywhere !
not 
"write once , compile anywhere"

c/c++可直接生成可执行程序

java生成`*.class`文件，不是可执行文件。java虚拟机去运行。

python是脚本语言。
与其他语言区别：脚本语言不需要更严格的语法。


**development language of most fundamental compter systems**
+ Linux
+ MySQL
+ OpenCV
+ TensorFlow , PyTorch
...

**high efficiency**
+ widely optimized compilers
+ access memory directly
+ excellent on computing



### compiler and link 

```c++
#include <iostream>
using namespace std;

int mul(int a , int b){
    return a * b;
}
//函数mul

int main(){
    int a , b;
    int result;
    cout << "pick two integers";
    cin >> a;
    cin >> b;

    result = mul(a , b);
    
    cout << "the result is " << result << endl;
    return 0;

}
//主函数中调用mul函数

```


**一般把函数的声明放在头文件里。
`*.h ; *.hpp`
把函数的实现/定义放在源文件。
`*.c *.cpp`**

![1683966319320](image/index/1683966319320.png)

main.cpp
![1683994787823](image/index/1683994787823.png)

mul.hpp
![1683994803831](image/index/1683994803831.png)

mul.cpp
![1683994814369](image/index/1683994814369.png)

```c
g++ -c main.cpp
g++ -c mul.cpp
//编译
g++ main.o mul.o -o mul
//链接

./mul
//please pick two nums 
//2 3
//6
```

### errors

**链接错误**
```c
#include "mul.cpp"

int Mul(int a , int b){
    return a * b;
}
//symbol not foudn 
//Function mul() is misspelled to Mul()
//此时在main.cpp找不到链接mul()，因为大小写
```

**运行错误runtime error**
```c
#include "mul.cpp"

int mul(int a , int b){
    int c = a / b;
    return a * b ;
}
//抛出异常
```

### 预处理preprocessor

![1683995334403](image/index/1683995334403.png)

![1683995418239](image/index/1683995418239.png)
PI不是一个变量，而是一个宏。


### 宏
理解：文字替换。
类似通过源代码的全文检索，进行全文替换。





### input & output
what is cout ?
```c
std::ostream cout;
```
+ std是一个命名空间（name space）。
```c
南方科技大学::黎明
深圳大学::黎明
```

**cin / cout**
c++风格的输入输出
operator
```c
cout << "hello" << endl
//endl 结束换行符
```

在c中：
```c
int v;
int ret = scanf("%d" , &v);
//&v取地址
```



————————分割线———————
### 为什么没有GUI?
graphical user interface

+ GUI is for human beings to interact with computers.
not all programs interact with human beings.
like DATABASE 

---

**command line arguments**

```c
int main(int argc , char **argv){
    //argc 参数个数
    // **argv参数数组
}
```



**每个变量声明时必须初始化变量**

## interger numbers

**overflow**
```c
int a = 56789;
int b = 56789;
int c = a * b;
cout c << endl;
//the output is a negative number!
//-1069976775
```
*why?*


**运算时一定要了解数值的取值范围**

### different data type for integer

### char
8-bit integer

+ signed char 
+ unsigned char
+ char

```c
char.cpp
char c1 = 'C';
char c2 = 80;
char c3 = 0x50;
//3个变量表达一样
```
**Chinese characters?**
+ char16
+ char32



### bool

```c
bool b1 = true;
int i = b1;
bool b2 = -256;
//b1 = true;
//i = 1;
//b2 = 1 (非0 即1)
```

+ 第一种 -老的类型定义#define
```c
typedef char bool;
#define true 1;
#define false 0;
```
+ 第二种 - 引`<stdbool.h>`库
  
**size_t**库

**fixed with integer types**
(since c++11)

defined in `<cstdint>
int8_t
int32_t
uinit16_t
...

**使用宏**

### floating point 
浮点数运算一直会带来微小误差。

处理误差in range 

![1684037114772](image/index/1684037114772.png)

```c
precision.cpp

float f1 = 2.34E+10f;
float f2 = f1 + 10;
//f1 - f2 = 0 (true)
```
原因：采样精度不够。
在取值范围内间隔采样。

**inf & nan**
无穷大和not a number


## arithmetic operators

**constant number**
```c
84// decimal
0135//octal
0x4F//hexadeximal
```
十六进制对程序员友好。

整数
```c
54//int 
43u//unsigned int
43l//long
43ul//unsigned long
43lu//unsigned long
```

浮点数
```c
3.43//3.43
3.2e23//3.2 x 10^23
```

**constant type qualifier常数限定符**

必须在初始化时定义
```c
const float PI = 3.32f;
PI += 1;//ERROR!
```

**auto(在C语言中可以，在c+中不建议做）**
不是数据类型，是一个placeholder。

输入后自动变成相应类型
```c
auto c = 2 ; //type of a is int 
auto be =  2.3 //type of be is double
```

![1684047407169](image/index/1684047407169.png)


**floating-point VS integers**
+ double operations is slower than float
+ lost precision


## if statement 
### if & if-else
```c
if num  = 10;
if(num < 5){
    cout << "the number is less than 5" << endl;
}
if(num == 5){
    cout << "the num is 5" <<endl;
}
else 
    cout << "the num is in range [4,10]" << endl;
```

**else跟最近的if配对**

### ? : operator
```c
bool isPositive = true;
int factor = 0;
//some operations may change isPositive's value 
factor = isPositive ? 1 : -1;
```

**condition**
what should be a condition?
```c
int num  = 10;
if(num < 5){
    cout << "the num is less than 5" <<endl;
} 
```
**the condition should be a expression which is convertible to bool !**

+ its value can be **bool/char/int/float**
+ 





**关系表达式**
![1684051380275](image/index/1684051380275.png)


**逻辑表达式**
![1684051346674](image/index/1684051346674.png)

**precedence**
! > && > ||

不确定时，加括号（优先级最高）

+ pointers are also frequently used as conditions 
  
```c
int * p = new int[1024];
if(!p){
    cout << "memory allocation failed" <<endl;
}
```

### while loop
syntax:
```c
while(expression){
    //...
}
```

```c
size_t num = 2;
while (num >= 0){
    cout << num << endl;
    num--;
}
//2
//1
//0
//18446744073708458...
```
原因：size_t 是一个无符号数，当num = 0时再--会变成range内最大的数死循环。
写成int ，问题解决。

```c
bool flag = true ;
int count = 0 ;
while(flag = true){
    cout << count++ <<endl;
    //and do sth
    if(count = 10)
    flag = false;
}
```













































