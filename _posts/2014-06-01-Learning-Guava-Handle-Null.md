---
layout: articles
title: Guava学习-Null的处理
tags: [java,Guava]
---
近期由于部门变动，被分到了一个新的项目中。只想感叹一句，终于有机会可以写代码了...从升本到现在工作1年，仔细算算已经有3年没有好好的写过代码了.工作的这一年中(省略)。接下来想利用参加这个新项目的机会，把前面学到的东西运用到实践中去。前些时候偶然发现了Guava这个东东。经过一些了解以后，不但刷新了我对编程的理解，也激起了我对函数式编程的兴趣。虽然用java来实现函数式编程问题还很多。但不妨碍Guava这个优秀的类库给程序的可读性、可维护性、可扩展性带来的提升。官方文档 [GuavaExplained](https://code.google.com/p/guava-libraries/wiki/GuavaExplained) 老是被墙 :(
<!--more-->

**在代码中常常需要处理对象为Null的情况**。然而这些处理逻辑很容易被遗漏掉，从而导致Bug的产生。如果利用Guava中提供的Optional类，则可以从一定程度上避免这种情况。例如：

1. 将方法的形参定义成Optional类，提醒接口的实现者处理参数为Null的情况。
2. 将返回值定义为Optional类，提醒方法的调用者处理返回值为Null的情况。

但Optional本身也是个对象，所以也可能为Null，这也算是一个隐患。可以使用@NotNull注解限制对象不为Null。

**在Guava中检查对象是否为Null**，可以使用Preconditions.checkNotNull(T)。如果你在eclipse里将Preconditions类配置成静态导入还可以增加代码的可读性，方便使用。并且checkNotNull的重载方法还支持变参的错误信息输出。其实Preconditions类对应于面向约定编程里的前置条件。

**Strings类中也有一些处理字符串为Null的方法**。但是要注意的是，不应该将Null和空字符串混为一谈。这样容易造成逻辑上的混乱，从而不便于维护和容易产生Bug。

**实现Object.equals方法时**，往往也要考虑对象为Null的情况。Guava中提供了Objects.equal方法来处理比较对象为Null的情况，对应于JDK7里的 Objects.equals 方法。

**使用NULL对象统一接口调用** 详见《重构》引入NULL对象一节。
使用起来其实还是有点麻烦，和编程习惯有关。
