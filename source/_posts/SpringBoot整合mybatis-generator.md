---
title: SpringBoot整合MyBatis Generator
date: 2020-02-16 12:37:16
tags:
	- Spring
	- SpringBoot
	- SpringBoot整合插件
categories:
	- Spring
	- SpringBoot
---

* MyBatis Generator是一款mybaits提供的代码生成器， MyBatis生成器（MyBatis Generator）能对数据库表内省，生成执行的增删改查（CRUD）时所需的MyBatis代码。

* SpringBoot与MyBatis Generator整合（with maven）

<!-- more -->

### [MyBatis Generator官方文档]( http://mybatis.org/generator/ )

> 建议使用时浏览官方文档

### 首先创建一个SpringBoot项目

> * 略过

### 引入MyBatis Generator插件

> * 在pom文件中引入插件（版本自己选择）
>
> ```
> <plugin>
>     <groupId>org.mybatis.generator</groupId>
>     <artifactId>mybatis-generator-maven-plugin</artifactId>
>     <version>1.4.0</version>
>     <dependencies>
>         <dependency>
>             <groupId>mysql</groupId>
>             <artifactId>mysql-connector-java</artifactId>
>             <version>${mysql.version}</version>
>         </dependency>
>     </dependencies>
> </plugin>
> ```
>
> * 创建generatorConfig.xml（默认位置为 ${basedir}/src/main/resources/generatorConfig.xml ）
>
> ```
> <?xml version="1.0" encoding="UTF-8"?>
> <!DOCTYPE generatorConfiguration
>         PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
>         "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">
> 
> <generatorConfiguration>
> 
>     <context id="DB2Tables" targetRuntime="MyBatis3">
>         <!-- 生成文件取消注释代码 -->
>         <commentGenerator>
>             <property name="suppressDate" value="true"/>
>             <property name="suppressAllComments" value="true"/>
>         </commentGenerator>
> 
>         <jdbcConnection driverClass="com.mysql.jdbc.Driver"
>                         connectionURL="jdbc:mysql:///imust_bbs"
>                         userId="root"
>                         password="root">
>         </jdbcConnection>
> 
>         <javaTypeResolver >
>             <property name="forceBigDecimals" value="false" />
>         </javaTypeResolver>
> 
>         <javaModelGenerator targetPackage="model所在包路径" targetProject="src/main/java">
>             <property name="enableSubPackages" value="true" />
>             <property name="trimStrings" value="true" />
>         </javaModelGenerator>
> 
>         <sqlMapGenerator targetPackage="mapperXML所在路径"  targetProject="src/main/resources">
>             <property name="enableSubPackages" value="true" />
>         </sqlMapGenerator>
> 
>         <javaClientGenerator type="XMLMAPPER" targetPackage="mapper所在包路径"  targetProject="src/main/java">
>             <property name="enableSubPackages" value="true" />
>         </javaClientGenerator>
> 
>         <table tableName="数据库表名" domainObjectName="Model类名" ></table>
>         <table tableName="user" domainObjectName="User" ></table>
> 
>     </context>
> </generatorConfiguration>
> 
> ```
>
> * 在application.yml中配置mapperXML与mapper的对应关系
>
> ```
> mybatis:
>   configuration:
>     # 驼峰命名
>     map-underscore-to-camel-case: true
>   type-aliases-package: mapper所在包路径
>   # mapperXML路径
>   mapper-locations: classpath:mapper/*.xml
> ```
>
> * 运行
>
> ```
> mvn -Dmybatis.generator.overwrite=true mybatis-generator:generate
> ```
>

### 其他更详细内容或其他引入方式请查看[MyBatis Generator官方文档]( http://mybatis.org/generator/index.html )

