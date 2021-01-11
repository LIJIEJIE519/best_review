# BJTU 院友会

## JWT

https://www.jianshu.com/p/576dbf44b2ae



## Shiro

### 1. 简介

https://www.w3cschool.cn/shiro/co4m1if2.html

Apache Shiro 是 Java 的一个安全框架。

![https://atts.w3cschool.cn/attachments/image/wk/shiro/1.png](https://atts.w3cschool.cn/attachments/image/wk/shiro/1.png)



**Authentication**：身份认证 / 登录，验证用户是不是拥有相应的身份；

**Authorization**：授权，即**权限验证**，验证某个已认证的用户是否拥有某个权限；即验证某个用户是否拥有**某个角色**；或者细粒度的验证某个用户对某个资源是否具有**某个权限**。

**Session** **Management**：会话管理，即用户登录后就是一次会话，在没有退出之前，它的所有信息都在会话中。

**Cryptography**：加密，保护数据的安全性，如**密码加密**存储到数据库，而不是明文存储。



### 2. 架构

![https://atts.w3cschool.cn/attachments/image/wk/shiro/2.png](https://atts.w3cschool.cn/attachments/image/wk/shiro/2.png)

直接交互的对象是 Subject，也就是说 Shiro 的**对外 API 核心**就是 Subject

**Subject**：主体，代表了当前 “用户”，这个用户不一定是一个具体的人，与当前应用交互的任何东西都是  Subject，如网络爬虫，机器人等；即一个抽象概念；所有 Subject 都绑定到 SecurityManager，与 Subject  的所有交互都会委托给 SecurityManager；可以把 Subject 认为是一个门面；SecurityManager 才是**实际的执行者**；

**SecurityManager**：安全管理器；即所有与安全有关的操作都会与 SecurityManager 交互；且它管理着所有 Subject；可以看出它是 Shiro 的核心，它负责与后边介绍的其他组件进行交互；

**Realm**：域，Shiro 从从 Realm **获取安全数据**（如用户、角色、权限），就是说  SecurityManager 要验证用户身份，那么它需要从 Realm 获取相应的用户进行比较**以确定用户身份是否合法**；也需要从 Realm  得到用户相应的**角色 / 权限进行验证**用户是否能进行操作；可以把 Realm 看成 DataSource，即安全数据源。

也就是说对于我们而言，最简单的一个 Shiro 应用：

1. 应用代码通过 Subject 来进行认证和授权，而 Subject 又委托给 SecurityManager；
2. 我们需要给 Shiro 的 SecurityManager 注入 Realm，从而让 SecurityManager 能得到合法的用户及其权限进行判断。

**从以上也可以看出，Shiro 不提供维护用户 / 权限，而是通过 Realm 让开发人员自己注入。**





### 2. 权限管理RBAC

#### 1. 基于资源的权限管理(Resource-Based Access Control) 

https://www.iteye.com/blog/globeeip-1236167







### BJTU做了什么

1. 做了权限异常处理





```
// swagger网址
http://49.234.4.204:8080/swagger-ui.html#/

jdbc:mysql://49.234.4.204:3306/schoolMate
username=schoolMate
password=Dmqbd@12
```



### GitHub引用

https://github.com/Heeexy/SpringBoot-Shiro-Vue

https://github.com/Smith-Cruise/Spring-Boot-Shiro





## spring

```xml

```





## mybatis

### 分页插件

1. PageHelper
2. https://github.com/pagehelper/Mybatis-PageHelper/blob/master/wikis/en/HowToUse.md