---
layout: post
Title: "重新认识hashCode()与equals"
Date: 2020-05-01 16:06:34.00000000 + 09:00
---

### 面试时，面试官可能会问你：”你重写过hashCode和equals么？为什么要重写equals时必须重写hashCode方法？“



#### hashCode()介绍

hashCode()的作用是获取哈希码，也称为散列码；它实际上是返回一个int整数。这个哈希码的作用是确定该对象在哈希表中的索引位置。hashCode()定义在JDK的Object.java中，这就意味着Java中的任何类都包含有hashCode()函数。

散列表存储的是键值对(key-value)，它的特点是：能根据“键”快速的检索出对应的“值”。这其中就利用到了散列码！



#### 为什么要有hashCode

##### 我们以“HashSet时，如何检查重复“为例子来说明为什么要有hashCode：

当你把对象加入HashSet时，HashSet会先计算对象的hashcode值来判断对象加入的位置，同时也会与其他已经加入的对象的hashcode值作比较，如果没有相符的hashcode，HashSet会假设对象没有重复出现。但是如果发现有相同hashcode值的对象，这时会调用equals()方法来检查hashcode相等的对象是否真的相同。如果两者相同，HashSet就不会让其加入操作成功。如果不同的话，就会重新散列到其他位置。这样我们就大大减少了equals的次数，相应就大大提高了执行速度。

### hashCode()与equals()的相关规定

1.如果两个对象相等，则hashcode一定也是相同的

2.两个对象相等，对两个对象分别调用equals方法都返回true

3.两个对象有相同的hashcode值，他们也不一定是相等的

4.equals方法被覆盖过，则hashcode方法也必须被覆盖

5.hashcode()的默认行为是对堆上的对象产生独特值。如果没有重写hashcode（），则该class的两个对象无论如何都不会相等（即使这两个对象指向相同的数据）。