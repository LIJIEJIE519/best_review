1. ### 骨架

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">

    <!--bean 即new对象-->
    <bean id="mysqlImpl" class="com.xjj.dao.UserDaoMySqlImpl"/>
    <bean id="OracleImpl" class="com.xjj.dao.UserDaoOracleImpl"/>
    
    <bean id="ServiceImpl" class="com.xjj.service.UserServiceImpl">
        <!--注意: 这里的name并不是属性 , 而是set方法后面的那部分 , 首字母小写-->
        <!--引用另外一个bean , 不是用value 而是用 ref-->
        <!--ref : 引用Spring容器中创建好的对象
            value:引用具体的值，基本数据类型
        -->
        <property name="userDao" ref="OracleImpl"/>
    </bean>

</beans>
```



2. ### 注解说明

   - @Autowird ：自动装配通过类型，@Qualifier(value="xxx")
   - @Nullable ：改字段可为null
   - @Resource ：自动装配，通过名字、类型
   - Component ：组件，放在类上，说明该类被Spring管理了，就是bean



### spring-dao.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
       http://www.springframework.org/schema/beans/spring-beans.xsd">

    <!--配置数据源：数据源有非常多，可以使用第三方的，也可使使用Spring的-->
    <bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
        <property name="driverClassName" value="com.mysql.jdbc.Driver"/>
        <property name="url" value="jdbc:mysql://localhost:3306/mybatis?useSSL=true&amp;useUnicode=true&amp;characterEncoding=utf8"/>
        <property name="username" value="root"/>
        <property name="password" value="123456"/>
    </bean>

    <!--SqlSessionFactory-->
    <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
        <property name="dataSource" ref="dataSource" />
        <!--关联Mybatis-->
        <property name="configLocation" value="classpath:mybatis-config.xml"/>
        <property name="mapperLocations" value="classpath:com/xjj/mapper/*.xml"/>
    </bean>

    <!--sqlSession-->
    <bean id="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
        <!--没有set方法：只能构造方法注入-->
        <constructor-arg index="0" ref="sqlSessionFactory" />
    </bean>

</beans>
```

