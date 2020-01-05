---
title: Java校招题(5)
date: 2020-01-05 09:24:17
tags:
	- Java基础
	- 面试
categories:
	- Java
---

* Java校招面试题目合集（五），随着做题复习各方面基础内容，提高自己从每一天做起！！！
* 题目来源与“牛客网”的“Java校招面试题目合集”的41-50题。

<!-- more -->

### [在Java中，对象什么时候可以被垃圾回收？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=41 )

> 当对象对当前使用这个对象的应用程序变得不可触及的时候(GC root 不可及) + 下次垃圾回收周期到来时，这个对象就可以被回收了。

### [JVM的永久代中会发生垃圾回收么？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=42 )

> 会，如果永久代满了或者是超过了临界值，会触发完全垃圾回收(Full GC)。如果你仔细查看垃圾收集器的输出信息，就会发现永久代也是被回收的。这就是为什么正确的永久代大小对避免Full GC是非常重要的原因。请参考下Java8：从永久代到元数据区
> (注：Java8中已经移除了永久代，新加了一个叫做元数据区的native内存区) 

### [Java中的两种异常类型是什么？他们有什么区别？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=43 )

> Java中有两种异常：受检查的(checked)异常和不受检查的(unchecked)异常。不受检查的异常不需要在方法或者是构造函数上声明，就算方法或者是构造函数的执行可能会抛出这样的异常，并且不受检查的异常可以传播到方法或者是构造函数的外面。相反，受检查的异常必须要用throws语句在方法或者是构造函数上声明。这里有Java异常处理的一些小建议。 

### [Java中Exception和Error有什么区别？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=44 )

>Exception和Error都是Throwable的子类。Exception用于用户程序可以捕获的异常情况。Error定义了不期望被用户程序捕获的异常。

### [throw和throws有什么区别？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=45 )

> 1、Throw用于方法内部，Throws用于方法声明上
>
> 2、Throw后跟异常对象，Throws后跟异常类型
>
> 3、Throw后只能跟一个异常对象，Throws后可以一次声明多种异常类型

### [异常处理完成以后，Exception对象会发生什么变化？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=46 )

> Exception对象会在下一个垃圾回收过程中被回收掉。

### [finally代码块和finalize()方法有什么区别？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=47 )

> 无论是否抛出异常，finally代码块都会执行，它主要是用来释放应用占用的资源。finalize()方法是Object类的一个protected方法，它是在对象被垃圾回收之前由Java虚拟机来调用的。
>

### [什么是Applet？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=48 )

> java applet是能够被包含在HTML页面中并且能被启用了java的客户端浏览器执行的程序。Applet主要用来创建动态交互的web应用程序。(能被浏览器执行的Java网页小程序，随网页被下载到客户端)

### [解释一下Applet的生命周期]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=49 )

> applet可以经历下面的状态：
>
> * Init：每次被载入的时候都会被初始化。
> * Start：开始执行applet。
> * Stop：结束执行applet。
> * Destroy：卸载applet之前，做最后的清理工作。 

### [当applet被载入的时候会发生什么？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=50 )

> 首先，创建applet控制类的实例，然后初始化applet，最后开始运行。

