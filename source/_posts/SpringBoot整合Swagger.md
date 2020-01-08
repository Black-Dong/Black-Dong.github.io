---
title: SpringBoot整合Swagger
date: 2020-01-08 18:02:48
tags:
	- Spring
	- SpringBoot
	- Swagger
categories:
	- Spring
	- SpringBoot
---

* Swagger是一款可以让你更方便、更流畅、更具格式化的书写API文档的框架。
* SpringBoot与Swagger整合。

<!-- more -->

### [Swagger官网]( https://swagger.io/ )

> 英语比较好的，可以看看官网。

### 首先创建一个SpringBoot的项目

> * 各种方式创建一个SpringBoot项目，此处不讲。
>

### 引入Swagger

> * 在pom文件中引入依赖(版本自己选择)
>
>   ```
>   <!-- swagger -->
>   <dependency>
>       <groupId>io.springfox</groupId>
>       <artifactId>springfox-swagger2</artifactId>
>       <version>2.7.0</version>
>   </dependency>
>   
>   <!-- swagger-ui 可视化的查看api -->
>   <dependency>
>       <groupId>io.springfox</groupId>
>       <artifactId>springfox-swagger-ui</artifactId>
>       <version>2.7.0</version>
>   </dependency>
>   ```
>
> * 编辑Swagger的配置类
>
>   ```
>   @Configuration
>   @EnableSwagger2
>   public class SwaggerConfig {
>   
>       @Bean
>       public Docket api(){
>           return new Docket(DocumentationType.SWAGGER_2)
>                   .select()
>                   .apis(RequestHandlerSelectors.any())
>                   .paths(PathSelectors.any())
>                   .build();
>       }
>   }
>   ```
>
> * Swagger常用注解
>
>   * Contoller相关注解
>
>     * @Api
>
>     |  注解属性   |   类型   |                描述                |
>     | :---------: | :------: | :--------------------------------: |
>     |    tags     | String[] |            控制器标签。            |
>     | description |  String  | 控制器描述（该字段被申明为过期）。 |
>
>   * 接口相关
>
>     * @ApiOperation
>
>     |  注解属性  |   类型   |      描述      |
>     | :--------: | :------: | :------------: |
>     |   value    |  String  |   接口说明。   |
>     |   notes    |  String  | 接口发布说明。 |
>     |    tags    | Stirng[] |     标签。     |
>     |  response  | Class<?> | 接口返回类型。 |
>     | httpMethod |  String  | 接口请求方式。 |
>     * @ApiIgnore: Swagger 文档不会显示拥有该注解的接口
>     * @ApilmplicitParams: 用于描述接口的非对象参数集
>     * @ApiImplicitParam: 用于描述接口的非对象参数，一般与 @ApiImplicitParams 组合使用
>
>     | 注解属性  | 描述                                                         |
>     | :-------: | :----------------------------------------------------------- |
>     | paramType | 查询参数类型，实际上就是参数放在那里。取值：path：以地址的形式提交数据，根据 id 查询用户的接口就是这种形式传参。query：Query string 的方式传参。header：以流的形式提交。form：以 Form 表单的形式提交。 |
>     | dataType  | 参数的数据类型。取值：Long、String                           |
>     |   name    | 参数名字。                                                   |
>     |   value   | 参数意义的描述。                                             |
>     | required  | 是否必填。取值：true：必填参数。false：非必填参数。          |
>
>   * Model相关接口
>
>     * @ApiModel: 可设置接口相关实体的描述。 
>     * @ApiModelProperty: 可设置实体属性的相关描述。 
>
>     | 注解属性        | 类型    | 描述                                                         |
>     | --------------- | ------- | ------------------------------------------------------------ |
>     | value           | String  | 字段说明。                                                   |
>     | name            | String  | 重写字段名称。                                               |
>     | dataType        | Stirng  | 重写字段类型。                                               |
>     | required        | boolean | 是否必填。                                                   |
>     | example         | Stirng  | 举例说明。                                                   |
>     | hidden          | boolean | 是否在文档中隐藏该字段。                                     |
>     | allowEmptyValue | boolean | 是否允许为空。                                               |
>     | allowableValues | String  | 该字段允许的值，当我们 API 的某个参数为枚举类型时，使用这个属性就可以清楚地告诉 API 使用者该参数所能允许传入的值。 |

### 推荐阅读[在 Spring Boot 项目中使用 Swagger 文档]( https://www.ibm.com/developerworks/cn/java/j-using-swagger-in-a-spring-boot-project/index.html )或[springboot快速集成swagger]( https://juejin.im/post/5cf08d65f265da1bb13f17a6#heading-14 )