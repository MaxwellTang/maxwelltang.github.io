---
layout:     post
title:      "Design Pattern Iteration"
subtitle:   "Iteration"
author:     "Jason Tang"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - 设计模式 迭代器 
---

> 迭代器用于对一个聚合对象进行遍历。通过引入迭代器可以将数据的遍历功能从聚合对象中分离出来，聚合对象只负责存储数据，而遍历数据有迭代器来完成。

##模式动机与定义

###模式动机

一个聚合对象应该提供一种方法让别人可以访问它的元素，而又不需要暴露他的内部结构。

###模式定义

迭代器提供一种方法来访问聚合对象，而不用暴露这个对象的内部表示，其别名为游标。迭代器模式是一种对象行为型模式。

