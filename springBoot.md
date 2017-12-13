# spring boot > spring cloud > 微服务
## 1、第一个springBoot程序
- 版本
> jdk 1.8.0_111 <br>
> maven 3.3.9 <br>
> 旗舰版 idea
- 创建一个程序
> 1、新建一个spring Initializr <br>
> 2、用注解的形式写一个类和方法  <br>
> 3、启动程序
## 2、自定义属性配置
> 1、配置文件 
>> application.properties 或 <br>
>> application.yml <br>

> 2、自定义属性（yml）
>> 1、`server  
      port: 8080
      context-path: /girl`
>> 2、` size: B` <br>
>> 类里定义 <br>
>> `@value("${size}")`<br>
>> `private String size;` <br>

>> 3、`context: "size: ${size}, age: ${age}"` 或 <br>
>> `girl: size: 8 age: 18` <br>
>> 定义一个girl类，两个参数，生成get、set方法 <br>
>> 使用 <br>
>> `@Autowired` <br>
>> `private Gril gril;`<br>

> 3、开发环境与生产环境不同配置的问题
>> 两个配置名分别是 application-dev.yml 和 application-prod.yml <br>
>> 新建一个application.yml配置文件 <br>
>> `spring: profiles: active: dev`--使用dev的配置文件

> 4、小结
>> @value 配置内容注入 <br>
>> @Component 分组配置注入<br>
>> @ConfigurationProperties 分组配置注入 <br>
## 3、Controller的使用
> 1、@Controller 处理http请求 <br>
>> 1、@PathVariable 获取url中的数据 新增EEEEEEE使用<br>
>> 2、@RequestParam 获取请求参数的值 查询使用<br>
>> 3、@GetMapping 组合注解 <br>

> 2、@RestController Spring4之后新加的注解，原来返回json需要@RespinseBody配合@Controller <br>
> 3、@RequestMapping 配置url映射
## 4、spring-data-jpa
> 1、jpa定义了一系列对象持久化的标准，实现这个规范的产品有Hibernate、TopLink等 <br>
> 2、简单的增删改查不用写一条sql
## 5、事物管理
> 1、@Transactional 注解
# 小结
- Spring Boot 介绍
- 安装
- 配置
- Controller的使用
- 数据库的操作
- 事物
