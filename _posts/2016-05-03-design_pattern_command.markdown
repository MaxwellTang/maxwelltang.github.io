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


> 命令模式是常用的行为型设计模式之一，它将请求发送者与请求接受者解耦，请求发送者通过命令对象来间接引用接受者，使得系统具有更好的灵活性，可以在不修改系统源代码的情况下将相同的发送者对应不同的接受者，也可以将多个命令对象组合成宏命令，还可以在命令类中提供用来撤销请求的方法。

##模式定义

Command Pattern：

> 将一个请求封装成一个对象，从而使我们可用不同的请求对客户进行参数化；对请求排队或者记录请求日志，以及支持可撤销的操作。命令模式是一种对象行为型模式，别名为动作模式或事务模式。

##模式结构与分析

###1.模式结构

命令模式包含如下角色：

![命令模式UML][1]

|角色|详细|
|--|--|
|Command|该类一般是一个接口，生命了用于执行请求的execute()等方法，通过这些方法可以调用请求接受者的相关操作|
|ConcreteCommand|该类是Command类的子类，实现了上述抽象类中声明的方法，它对应具体的接收者对象，绑定接收者对象的动作。在实现execute()方法时，将调用接受者对象的相关操作。
|Invoker|至于Command类存在关联关系。在程序运行时将调用具体命令对象的execute()方法，间接调用接收者的相关操作。|
|Receiver|接受者执行与请求相关的操作，它具体实现对请求的业务处理。|
|Client|在Client类中需要创建发送者对象和具体命令类对象，在创建具体命令对象时指定其对应的接受者，发送者与接受者之间无直接关系，通过具体命令对象实现间接调用。|


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
