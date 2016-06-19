---
layout:     post
title:      "C++11新特性-auto"
subtitle:   "C++11"
author:     "Jason Tang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - C++
---
 

> C++11中引入的auto主要有两种用途：自动类型推断和返回值占位。
 
## 自动类型推断
 
auto自动类型推断可从初始化表达式中推断出变量的数据类型。
 
```C++
auto a = 10;
auto b = 'A';
auto s("hello");
```
 
## 返回值占位
 
```C++
auto sample(S1 Var1,S2 Var2)
{
 return Var1+Var2;
}
```
 
## 注意
 
- auto是一个占位符，并不是一个数据类型，因此不能用于类型转换或其他相关操作，例如sizeof。
- 函数和模板的参数不能声明为auto
- auto不能与其它类型组合连用

