---
title: C++学习笔记-异常处理
date: 2020-4-18
tags: 
- demo
categories:
- [学习, C加加]
---
# 必备知识 #
异常是程序在执行期间产生的问题。C++ 异常是指在程序运行时发生的特殊情况，比如尝试除以零的操作。异常提供了一种转移程序控制权的方式。C++ 异常处理涉及到三个关键字：try、catch、throw。  
- throw: 当问题出现时，程序会抛出一个异常。这是通过使用 throw 关键字来完成的。
- catch: 在您想要处理问题的地方，通过异常处理程序捕获异常。catch 关键字用于捕获异常。
- try: try 块中的代码标识将被激活的特定异常。它后面通常跟着一个或多个 catch 块。

**C++ 标准的异常**
![](https://i.loli.net/2020/04/18/QNH9BCKMFbAfLqm.png)

异常|	描述
:- |:-
std::exception|	该异常是所有标准 C++ 异常的父类。
std::bad_alloc	|该异常可以通过 new 抛出。
std::bad_cast	|该异常可以通过 dynamic_cast 抛出。
std::bad_exception	|这在处理 C++ 程序中无法预期的异常时非常有用。
std::bad_typeid	|该异常可以通过 typeid 抛出。
std::logic_error	|理论上可以通过读取代码来检测到的异常。
std::domain_error	|当使用了一个无效的数学域时，会抛出该异常。
std::invalid_argument	|当使用了无效的参数时，会抛出该异常。
std::length_error	|当创建了太长的 std::string 时，会抛出该异常。
std::out_of_range	|该异常可以通过方法抛出，例如 std::vector 和 std::bitset<>::operator[]()。
std::runtime_error	|理论上不可以通过读取代码来检测到的异常。
std::overflow_error	|当发生数学上溢时，会抛出该异常。
std::range_error	|当尝试存储超出范围的值时，会抛出该异常。
std::underflow_error	|当发生数学下溢时，会抛出该异常。

# 技能学习 #
## 处理多个异常 ##
如果 try 块在不同的情境下会抛出不同的异常，这个时候可以尝试罗列多个 catch 语句，用于捕获不同类型的异常
```
try
{
   // 保护代码
}catch( ExceptionName e1 )
{
   // catch 块
}catch( ExceptionName e2 )
{
   // catch 块
}catch( ExceptionName eN )
{
   // catch 块
}
```
## 手动抛出异常 ##
您可以使用 throw 语句在代码块中的任何地方抛出异常。throw 语句的操作数可以是任意的表达式，表达式的结果的类型决定了抛出的异常的类型。  
抛出了一个类型为 const char* 的异常，因此，当捕获该异常时，我们必须在 catch 块中使用 const char*
```
#include <iostream>
using namespace std;
 
double division(int a, int b)
{
   if( b == 0 )
   {
      throw "Division by zero condition!";
   }
   return (a/b);
}
 
int main ()
{
   int x = 50;
   int y = 0;
   double z = 0;
 
   try {
     z = division(x, y);
     cout << z << endl;
   }catch (const char* msg) {
     cerr << msg << endl;
   }
 
   return 0;
}
```
## 自定义异常 ##
您可以通过继承和重载 exception 类来定义新的异常。下面的实例演示了如何使用 std::exception 类来实现自己的异常：
```
#include <iostream>
#include <exception>
using namespace std;
 
struct MyException : public exception
{
  const char * what () const throw ()
  {
    return "C++ Exception";
  }
};
 
int main()
{
  try
  {
    throw MyException();
  }
  catch(MyException& e)
  {
    std::cout << "MyException caught" << std::endl;
    std::cout << e.what() << std::endl;
  }
  catch(std::exception& e)
  {
    //其他的错误
  }
}
```
##  ##

##  ##
# 工具推荐 #
- 菜鸟教程在线C++编辑器
[https://www.runoob.com/try/runcode.php?filename=helloworld&type=cpp](https://www.runoob.com/try/runcode.php?filename=helloworld&type=cpp)




---
<center>
<table>
    <tr>
        <td >
            <center>
                <img src="https://i.loli.net/2020/01/08/CJz85Sbal6M7EOV.png" width="200"/>
            </center>
            <center style="font-weight:900">
                微信：宏沉一笑
            </center>
        </td>
        <td >
            <center>
                <img src="https://i.loli.net/2020/01/08/veq2DSphHME9KPV.jpg" width="200"/>
            </center>
            <center style="font-weight:900">
                公众号：漫步之行
            </center>
        </td>
    </tr>
</table>
</center>


**签名：Smile every day**    
**名字：宏沉一笑**   
**邮箱：whghcyx@outlook.com**  
**个人网站：https://whg555.github.io**  
---
