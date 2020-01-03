---
title: Java校招题(2)
date: 2020-01-02 13:27:44
tags:
	- Java基础
	- 面试题
categories:
	- Java
---

* Java校招面试题目合集（二），随着做题复习各方面基础内容，提高自己从每一天做起！！！

* 题目来源于“牛客网”的“Java校招面试题目合集”的11-20题。

  

<!-- more -->

### [进程和线程的区别是什么？]( https://www.nowcoder.com/ta/review-java/review?tpId=31&tqId=21069&query=&asc=true&order=&page=11 ) 

> 进程是执行着的应用程序，而线程是进程内部的一个执行序列。一个进程可以有多个线程。线程又叫做轻量级进程。
>
> **线程与进程的区别归纳：**
>
> **a.地址空间和其它资源**：进程间相互独立，同一进程的各线程间共享。某进程内的线程在其它进程不可见。
>
> **b.通信：**进程间通信IPC，线程间可以直接读写进程数据段（如全局变量）来进行通信——需要进程同步和互斥手段的辅助，以保证数据的一致性。
>
> **c.调度和切换**：线程上下文切换比进程上下文切换要快得多。
>
> d.在多线程OS中，进程不是一个可执行的实体。

### [创建线程有几种不同的方式？你喜欢哪一种？为什么？]( https://www.nowcoder.com/ta/review-java/review?page=12 )

> 有4种方式可以用来创建线程：
>
> * 继承Thread类
>
> * 实现Runnable接口
>
> * 应用程序可以使用Executor框架来创建线程池
>
> 实现Runnable接口这种方式更受欢迎，因为这不需要继承Thread类。在应用设计中已经继承了别的对象的情况下，这需要多继承（而Java不支持多继承），只能实现接口。同时，线程池也是非常高效的，很容易实现和使用。 
>
> * 还有一种方式是实现Callable接口

### [概括的解释下线程的几种可用状态。]( https://www.nowcoder.com/ta/review-java/review?page=13 )

> 1. 新建( new )：新创建了一个线程对象。
>
> 2. 可运行( runnable )：线程对象创建后，其他线程(比如 main 线程）调用了该对象 的 start ()方法。该状态的线程位于可运行线程池中，等待被线程调度选中，获 取 cpu 的使用权 。
>
> 3. 运行( running )：可运行状态( runnable )的线程获得了 cpu 时间片（ timeslice ） ，执行程序代码。
>
> 4. 阻塞( block )：阻塞状态是指线程因为某种原因放弃了 cpu 使用权，也即让出了 cpu timeslice ，暂时停止运行。直到线程进入可运行( runnable )状态，才有 机会再次获得 cpu timeslice 转到运行( running )状态。阻塞的情况分三种：
>   (一). 等待阻塞：运行( running )的线程执行 o . wait ()方法， JVM 会把该线程放 入等待队列( waitting queue )中。
>   (二). 同步阻塞：运行( running )的线程在获取对象的同步锁时，若该同步锁 被别的线程占用，则 JVM 会把该线程放入锁池( lock pool )中。
>   (三). 其他阻塞: 运行( running )的线程执行 Thread . sleep ( long ms )或 t . join ()方法，或者发出了 I / O 请求时， JVM 会把该线程置为阻塞状态。            当 sleep ()状态超时、 join ()等待线程终止或者超时、或者 I / O 处理完毕时，线程重新转入可运行( runnable )状态。
>
> 5. 死亡( dead )：线程 run ()、 main () 方法执行结束，或者因异常退出了 run ()方法，则该线程结束生命周期。死亡的线程不可再次复生。
>
>    ![Java校招题(2)_线程状态图](http://black-dong.oss-cn-beijing.aliyuncs.com/blog/Java%E6%A0%A1%E6%8B%9B%E9%A2%98(2)_%E7%BA%BF%E7%A8%8B%E7%8A%B6%E6%80%81%E5%9B%BE.png)

### [同步方法和同步代码块的区别是什么？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=14 )

> 区别：
>
> * 同步方法默认用this或者当前类class对象作为锁；
>
> * 同步代码块可以选择以什么来加锁，比同步方法要更细颗粒度，我们可以选择只同步会发生同步问题的部分代码而不是整个方法；
>
> * 同步方法使用关键字 synchronized修饰方法，而同步代码块主要是修饰需要进行同步的代码，用  synchronized（object）{代码内容}进行修饰；

### [在监视器(Monitor)内部，是如何做线程同步的？程序应该做哪种级别的同步？](  https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=15 )

>  监视器和锁在Java虚拟机中是一块使用的。监视器监视一块同步代码块，确保一次只有一个线程执行同步代码块。每一个监视器都和一个对象引用相关联。线程在获取锁之前不允许执行同步代码。 

### [ 什么是死锁(deadlock)？ ]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=16 )

>所谓死锁是指多个进程因竞争资源而造成的一种僵局（互相等待），若无外力作用，这些进程都将无法向前推进。死锁产生的4个必要条件：
>
>- 互斥条件：进程要求对所分配的资源（如打印机）进行排他性控制，即在一段时间内某资源仅为一个进程所占有。此时若有其他进程请求该资源，则请求进程只能等待。
>- 不剥夺条件：进程所获得的资源在未使用完毕之前，不能被其他进程强行夺走，即只能由获得该资源的进程自己来释放（只能是主动释放)。
>- 请求和保持条件：进程已经保持了至少一个资源，但又提出了新的资源请求，而该资源 已被其他进程占有，此时请求进程被阻塞，但对自己已获得的资源保持不放。
>- 循环等待条件：存在一种进程资源的循环等待链，链中每一个进程已获得的资源同时被 链中下一个进程所请求。

### [如何确保N个线程可以访问N个资源同时又不导致死锁？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=17 )

> 使用多线程的时候，一种非常简单的避免死锁的方式就是：指定获取锁的顺序，并强制线程按照指定的顺序获取锁。因此，如果所有的线程都是以同样的顺序加锁和释放锁，就不会出现死锁了。 

### [Java集合类框架的基本接口有哪些？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=18 )

>  集合类接口指定了一组叫做元素的对象。集合类接口的每一种具体的实现类都可以选择以它自己的方式对元素进行保存和排序。有的集合类允许重复的键，有些不允许。
> Java集合类提供了一套设计良好的支持对一组对象进行操作的接口和类。Java集合类里面最基本的接口有：
>
> * Collection：代表一组对象，每一个对象都是它的子元素。
> * Set：不包含重复元素的Collection。
> * List：有顺序的collection，并且可以包含重复元素。
> * Map：可以把键(key)映射到值(value)的对象，键不能重复。 

### [为什么集合类没有实现Cloneable和Serializable接口？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=19 )

> 克隆(cloning)或者是序列化(serialization)的语义和含义是跟具体的实现相关的。因此，应该由集合类的具体实现来决定如何被克隆或者是序列化。

### [什么是迭代器(Iterator)？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=20 )

> Iterator接口提供了很多对集合元素进行迭代的方法。每一个集合类都包含了可以返回迭代器实例的迭代方法。迭代器可以在迭代的过程中删除底层集合的元素,但是不可以直接调用集合的remove(Object Obj)删除，可以通过迭代器的remove()方法删除。

