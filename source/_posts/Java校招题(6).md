---
title: Java校招题(其他)
date: 2020-01-05 11:01:48
tags:
	- Java基础
	- 面试题
categories:
	- Java
	- Java 基础
---

* Java校招面试题目合集（六），随着做题复习各方面基础内容，提高自己从每一天做起！！！
* 题目来源与“牛客网”的“Java校招面试题目合集” ，需要跟多该主题下内容请到[ Java校招面试题目合集 ]( https://www.nowcoder.com/ta/review-java?query=&asc=true&order=&tagQuery=&page=1 )

<!-- more -->

### [什么是JDBC？]( https://www.nowcoder.com/ta/review-java/review?tpId=31&tqId=21145&query=&asc=true&order=&page=72 )

> JDBC是允许用户在不同数据库之间做选择的一个抽象层。JDBC允许开发者用JAVA写数据库应用程序，而不需要关心底层特定数据库的细节，是一种API。



### [解释下驱动(Driver)在JDBC中的角色。]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=73 )

> JDBC驱动提供了特定厂商对JDBC API接口类的实现，驱动必须要提供java.sql包下面这些类的实现：Connection, Statement, PreparedStatement,CallableStatement, ResultSet和Driver。 

### [ Class.forName()方法有什么作用？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=74 )

> 初始化参数指定的类，并且返回此类对应的Class 对象

### [PreparedStatement比Statement有什么优势？]( https://www.nowcoder.com/ta/review-java/review?query=&asc=true&order=&page=75 )

>PreparedStatements是预编译的，因此，性能会更好。同时，不同的查询参数值，PreparedStatement可以重用。
