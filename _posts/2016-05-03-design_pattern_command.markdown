---
layout:     post
title:      "Design Pattern 命令模式"
subtitle:   "命令模式"
author:     "Jason Tang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 设计模式 命令模式 
---



###2.模式分析
典型的Command类代码：
```java
public abstract class Command
{
    public abstract void execute();
}
```
典型的Invoker类代码：
```java
public class Invoker
{
    private Command command;
    public Invoker(Command command)
    {
        this.command = commmand;
    }
    public void setCommand(Command command)
    {
        this.command = command;
    }
    public void call()
    {
        command.execute();
    }
}
```
典型的ConcreteCommand类代码：
```java
public class ConcreteCommand extends Command
{
    private Receiver receiver;
    public void execute()
    {
        receiver.action();
    }
}
```
典型的Receiver类代码：
```java
public class Receiver
{
    public void action()
    {
        //具体操作
    }
}
```

##命令模式扩展
###撤销操作的实现
> 对Command类进行修改使得系统支持撤销操作和恢复操作

简单的例子：
```java
public abstract class Command
{
    public abstract void execute();
    public abstract void undo();
}
```
###宏命令
> 宏命令又称组合命令，它是命令模式和组合模式联合的产物。宏命令也是一个ConcreteCommand，但是它包含了对其他Command对象的引用。


  [1]: http://i2.piimg.com/e4705e901fadfb2e.png
