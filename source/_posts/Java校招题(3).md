---
title: Java校招题(3)
date: 2020-01-03 07:05:18
tags:
	- Java基础
	- 面试题
categories:
	- Java
	- Java 基础
---

* Java校招面试题目合集（三），随着做题复习各方面基础内容，提高自己从每一天做起！！！
* 题目来源与“牛客网”的“Java校招面试题目合集”的21-30题。

<!-- more -->

### [Iterator和ListIterator的区别是什么？]( https://www.nowcoder.com/ta/review-java/review?page=21 )

>  下面列出了他们的区别：
>
> * Iterator可用来遍历Set和List集合，但是ListIterator只能用来遍历List。
> * Iterator对集合只能是前向遍历，ListIterator既可以前向也可以后向。
> * ListIterator实现了Iterator接口，并包含其他的功能，比如：增加元素，替换元素，获取前一个和后一个元素的索引，等等。 

### [快速失败(fail-fast)和安全失败(fail-safe)的区别是什么？]( https://www.nowcoder.com/ta/review-java/review?page=22 )

> 一：快速失败（fail—fast）
>
> * 在用迭代器遍历一个集合对象时，如果遍历过程中对集合对象的结构进行了修改（增加、删除），则会抛出Concurrent Modification Exception。
>
> * 原理：迭代器在遍历时直接访问集合中的内容，并且在遍历过程中使用一个 modCount 变量。集合在被遍历期间如果结构发生变化，就会改变modCount的值。每当迭代器使用hashNext()/next()遍历下一个元素之前，都会检测modCount变量是否为expectedmodCount值，是的话就返回遍历；否则抛出异常，终止遍历。
>
> * 注意：这里异常的抛出条件是检测到 modCount！=expectedmodCount 这个条件。如果集合发生变化时修改modCount值刚好又设置为了expectedmodCount值，则异常不会抛出。因此，不能依赖于这个异常是否抛出而进行并发操作的编程，这个异常只建议用于检测并发修改的bug。
>
> * 场景：java.util包下的集合类都是快速失败的，不能在多线程下发生并发修改（迭代过程中被修改）。
>
> 二：安全失败（fail—safe）
>
> * 采用安全失败机制的集合容器，在遍历时不是直接在集合内容上访问的，而是先复制原有集合内容，在拷贝的集合上进行遍历。
>
> * 原理：由于迭代时是对原集合的拷贝进行遍历，所以在遍历过程中对原集合所作的修改并不能被迭代器检测到，所以不会触发Concurrent Modification Exception。
>
> * 缺点：基于拷贝内容的优点是避免了Concurrent Modification Exception，但同样地，迭代器并不能访问到修改后的内容，即：迭代器遍历的是开始遍历那一刻拿到的集合拷贝，在遍历期间原集合发生的修改迭代器是不知道的。
>
> * 场景：java.util.concurrent包下的容器都是安全失败，可以在多线程下并发使用，并发修改。

### [Java中的HashMap的工作原理是什么？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=23 )

>  Java中的HashMap是以键值对(key-value)的形式存储元素的。
>
> HashMap需要一个hash函数，它使用hashCode()和equals()方法来向集合/从集合添加和检索元素。当调用put()方法的时候，HashMap会计算key的hash值，然后把键值对存储在集合中合适的索引上。如果key已经存在了，value会被更新成新值。
>
> HashMap的一些重要的特性是它的容量(capacity 默认16)，负载因子(load factor 默认0.75)和扩容极限(threshold resizing)。 

### [hashCode()和equals()方法的重要性体现在什么地方？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=24 )

>  Java中的HashMap使用hashCode()和equals()方法来确定键值对的索引，当根据键获取值的时候也会用到这两个方法。如果没有正确的实现这两个方法，两个不同的键可能会有相同的hash值，因此，可能会被集合认为是相等的。而且，这两个方法也用来发现重复元素。所以这两个方法的实现对HashMap的精确性和正确性是至关重要的。 

### [HashMap和Hashtable有什么区别？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=25 )

> HashMap和Hashtable都实现了Map接口，因此很多特性非常相似。但是，他们有以下不同点：
>
> * HashMap允许键和值是null，而Hashtable不允许键或者值是null。
> * Hashtable是同步的，而HashMap不是。因此，HashMap更适合于单线程环境，而Hashtable适合于多线程环境。
> * HashMap提供了可供应用迭代的键的集合，因此，HashMap是快速失败的。另一方面，Hashtable提供了对键的列举(Enumeration)。
> * 一般认为Hashtable是一个遗留的类。 

### [数组(Array)和列表(ArrayList)有什么区别？什么时候应该使用Array而不是ArrayList？]( https://www.nowcoder.com/ta/review-java/review?page=26 )

> 下面列出了Array和ArrayList的不同点：
>
> * Array可以包含基本类型和对象类型，ArrayList只能包含对象类型。
> * Array大小是固定的，ArrayList的大小是动态变化的。
> * ArrayList提供了更多的方法和特性，比如：addAll()，removeAll()，iterator()等等。
> * 对于基本类型数据，集合使用自动装箱来减少编码工作量。但是，当处理固定大小的基本数据类型的时候，这种方式相对比较慢。 

### [ArrayList和LinkedList有什么区别？]( https://www.nowcoder.com/ta/review-java/review?page=27 )

> ArrayList和LinkedList都实现了List接口，他们有以下的不同点：
>
> * ArrayList是基于索引的数据接口，它的底层是数组。它可以以O(1)时间复杂度对元素进行随机访问。与此对应，LinkedList是以元素列表的形式存储它的数据，每一个元素都和它的前一个和后一个元素链接在一起，在这种情况下，查找某个元素的时间复杂度是O(n)。
> * 相对于ArrayList，LinkedList的插入，添加，删除操作速度更快，因为当元素被添加到集合任意位置的时候，不需要像数组那样重新计算大小或者是更新索引。
> * LinkedList比ArrayList更占内存，因为LinkedList为每一个节点存储了两个引用，一个指向前一个元素，一个指向下一个元素。
> * 也可以参考ArrayList vs. LinkedList。 

### [Comparable和Comparator接口是干什么的？列出它们的区别。]( https://www.nowcoder.com/ta/review-java/review?page=28 )

> Java提供了只包含一个compareTo()方法的Comparable接口。
>
> * 这个方法可以个给两个对象排序。具体来说，它返回负数，0，正数来表明已经存在的对象小于，等于，大于输入对象。
>
> Java提供了包含compare()和equals()两个方法的Comparator接口。
>
> * compare()方法用来给两个输入参数排序，返回负数，0，正数表明第一个参数是小于，等于，大于第二个参数。
> * equals()方法需要一个对象作为参数，它用来决定输入参数是否和comparator相等。只有当输入参数也是一个comparator并且输入参数和当前comparator的排序结果是相同的时候，这个方法才返回true。 

### [什么是Java优先级队列(Priority Queue)？]( https://www.nowcoder.com/ta/review-java/review?page=29 )

> PriorityQueue是一个基于优先级堆的无界队列，它的元素是按照自然顺序(natural order)排序的。在创建的时候，我们可以给它提供一个负责给元素排序的比较器。PriorityQueue不允许null值，因为他们没有自然顺序，或者说他们没有任何的相关联的比较器。最后，PriorityQueue不是线程安全的，入队和出队的时间复杂度是O(log(n))。

### [你了解大O符号(big-O notation)么？你能给出不同数据结构的例子么？]( https://www.nowcoder.com/ta/review-java/review?page=30 )

> 大O符号描述了当数据结构里面的元素增加的时候，算法的规模或者是一个渐进上界 。
> 大O符号也可用来描述其他的行为，比如：内存消耗。因为集合类实际上是数据结构，我们一般使用大O符号基于时间，内存和性能来选择最好的实现。大O符号可以对大量数据的性能给出一个很好的说明。 
