---
title: Java校招题(4)
date: 2020-01-04 15:17:07
tags:
	- Java基础
	- 面试题
categories:
	- Java
---

* Java校招面试题目合集（四），随着做题复习各方面基础内容，提高自己从每一天做起！！！
* 题目来源与“牛客网”的“Java校招面试题目合集”的31-40题。

<!-- more -->

### [ 如何权衡是使用无序的数组还是有序的数组？ ](https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=31)

> 有序数组最大的好处在于查找的时间复杂度是O(log n)，而无序数组是O(n)。
>
> 有序数组的缺点是插入操作的时间复杂度是O(n)，因为值大的元素需要往后移动来给新元素腾位置。相反，无序数组的插入时间复杂度是常量O(1)。 

### [ Java集合类框架的最佳实践有哪些？ ](https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=32)

> 根据应用的需要正确选择要使用的集合的类型对性能非常重要，比如：假如元素的数量是固定的，而且能事先知道，我们就应该用Array而不是ArrayList。
>
> 有些集合类允许指定初始容量。因此，如果我们能估计出存储的元素的数目，我们可以设置初始容量来避免重新计算hash值或者是扩容。
>
> 为了类型安全，可读性和健壮性的原因总是要使用泛型。同时，使用泛型还可以避免运行时的ClassCastException。
>
> 使用JDK提供的不变类(immutable class)作为Map的键可以避免为我们自己的类实现hashCode()和equals()方法。
>
> 编程的时候接口优于实现。
>
> 底层的集合实际上是空的情况下，返回长度是0的集合或者是数组，不要返回null。 

### [ Enumeration接口和Iterator接口的区别有哪些？ ](https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=33)

> Enumeration速度是Iterator的2倍，同时占用更少的内存。但是，Iterator远远比Enumeration安全，因为其他线程不能够修改正在被iterator遍历的集合里面的对象（即Iterator为fail-fast）。同时，Iterator允许调用者删除底层集合里面的元素，这对Enumeration来说是不可能的。 

### [ HashSet和TreeSet有什么区别？ ](https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=34)

> HashSet是由一个hash表来实现的，因此，它的元素是无序的。add()，remove()，contains()方法的时间复杂度是O(1)。
>
> 另一方面，TreeSet是由一个树形的结构来实现的，它里面的元素是有序的（如果需要在Treeset中插入对对象，需要实现Comparable接口或传入Comparator，为其指定比较策略）。因此，add()，remove()，contains()方法的时间复杂度是O(logn)。

### [Java中垃圾回收有什么目的？什么时候进行垃圾回收？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=35 )

> 垃圾回收是在内存中存在没有引用的对象或超过作用域的对象时进行。
>
> 垃圾回收的目的是识别并且丢弃应用不再使用的对象来释放和重用资源。
>
> 回收时间：即触发GC的时间，在新生代的Eden区满了，会触发新生代GC（Mimor    GC），经过多次触发新生代GC存活下来的对象就会升级到老年代，升级到老年代的对象所需的内存大于老年代剩余的内存，则会触发老年代GC（Full    GC）。当程序调用System.gc()时也会触发Full GC。

### [System.gc()和Runtime.getRuntime().gc();会做什么事情？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=36 )

> 这两个方法用来提示JVM要进行垃圾回收。但是，立即开始还是延迟进行垃圾回收是取决于JVM的。

### [finalize()方法什么时候被调用？析构函数(finalization)的目的是什么？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=37 )

> 垃圾回收器(garbage collector)决定回收某对象时，就会运行该对象的finalize()方法 但是在Java中很不幸，如果内存总是充足的，那么垃圾回收可能永远不会进行，也就是说finalize()可能永远不被执行，显然指望它做收尾工作是靠不住的。 那么finalize()究竟是做什么的呢？它最主要的用途是回收特殊渠道申请的内存。Java程序有垃圾回收器，所以一般情况下内存问题不用程序员操心。但有一种JNI(Java Native Interface)调用non-Java程序（C或C++），finalize()的工作就是回收这部分的内存。 

### [如果对象的引用被置为null，垃圾收集器是否会立即释放对象占用的内存？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=38 )

> 不会，在下一个垃圾回收周期中，这个对象将是可被回收的。

### [ Java堆的结构是什么样子的？什么是堆中的永久代(Perm Gen space)? ](https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=39)

> JVM的堆是运行时数据区，所有类的实例和数组都是在堆上分配内存。它在JVM启动的时候被创建。对象所占的堆内存是由自动内存管理系统也就是垃圾收集器回收。
>
> 堆内存是由存活和死亡的对象组成的。存活的对象是应用可以访问的，不会被垃圾回收。死亡的对象是应用不可访问尚且还没有被垃圾收集器回收掉的对象。一直到垃圾收集器把这些对象回收掉之前，他们会一直占据堆内存空间。  
>
> 永久代是用于存放静态文件，如Java类、方法等。持久代对垃圾回收没有显著影响，但是有些应用可能动态生成或者调用一些class，例如Hibernate  等，在这种时候需要设置一个比较大的持久代空间来存放这些运行过程中新增的类，永久代中一般包含： 
>
> -    类的方法(字节码...)  
> -    类名(Sring对象)  
> -    .class文件读到的常量信息  
> -    class对象相关的对象列表和类型列表 (e.g., 方法对象的array).  
> -    JVM创建的内部对象  
> -    JIT编译器优化用的信息 

### [ 串行(serial)收集器和吞吐量(throughput)收集器的区别是什么？ ](https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=40)

> 吞吐量收集器使用并行版本的新生代垃圾收集器，它用于中等规模和大规模数据的应用程序。而串行收集器对大多数的小应用(在现代处理器上需要大概100M左右的内存)就足够了。 
>
> 链接：https://www.nowcoder.com/questionTerminal/46b6030921164ab0a3cb3dbd6d64f01a来源：牛客网
>
> ### Serial 收集器
>
> - Serial 收集器是历史悠久，最基本的收集器。它是一个单线程的收集器（说明：这里的单线程不仅仅是指收集器工作时使用一个CPU或者一条收集线程去收集，并且Serial工作时，必须暂停其他所有的工作线程，也就是“stop the world”，直到垃圾收集完成。）Serial是JVM运行在Client模式默认的新生代收集器。
>
> ### throughput收集器
>
> - 也叫做Parallel Scavenge 收集器，它的目标是达到一个可控制的吞吐量(throughput)，（说明：吞吐量就是CPU用于执行代码的时间和CPU总共消耗时间的比值，即：吞吐量 = 运行代码时间 / (运行代码时间 + 垃圾收集器工作时间)），JVM提供了两个参数以精确的控制吞吐量，-XX:MaxGCPauseMillis 最大收集停顿时间；-XX:GCTimeRatio 垃圾收集时间占总时间的比例。
>
> ### 总结
>
> - 了解了他们各自的特性，那么他们之间的不同点就显而易见了，Serial收集器工作时 "stop the world",简单而高效。而throughput收集器更关注总体的吞吐量，收集效果和性能总是密切关联的。