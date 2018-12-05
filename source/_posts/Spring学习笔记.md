---
title: Spring学习笔记
date: 2018-12-05 15:52:28
tags: 学习笔记
---

# Spring学习笔记

## 1. Spring概念

- spring是开源的轻量级框架
- spring核心主要两部分
  - aop：面向切面编程，扩展功能不是修改源代码实现
  - ioc：控制反转，比如有一个类，在类里面有方法（不是静态的方法），以前调用类里面的方法需要创建类的对象，使用对象来调用方法，创建类对象的过程，需要new出来对象，Ioc就是把对象的创建不是通过new方式实现，而是交给spring配置创建类对象
- spring是一站式框架
  - spring在javaee三层结构中，每一层都提供不同的解决技术
    - web层：springMVC
    - service层：spring的ioc
    - dao层：spring的jdbcTemplate 

## 2. Spring的ioc操作

- 把对象的创建交给spring进行管理
- ioc的两种操作方式
  - ioc的配置文件方式
  - ioc的注解方式

## 3. IoC底层原理

- ioc底层原理使用技术
  - xml配置文件
  - dom4j解析xml
  - 工厂设计模式
  - 反射
    ![ioc底层原理](https://img-blog.csdnimg.cn/20181030001454415.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80MjA1MzM2MQ==,size_16,color_FFFFFF,t_70)

## 4. IoC入门案例

1. 通过idea创建maven项目，引入spring框架

   ```xml
   <properties>
       <!-- spring版本号 -->
       <spring.version>4.3.20.RELEASE</spring.version>
       <!-- log4j日志文件管理包版本 -->
       <slf4j.version>1.7.7</slf4j.version>
       <log4j.version>1.2.17</log4j.version>
   </properties>
   <!-- spring核心包 -->
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-core</artifactId>
       <version>${spring.version}</version>
   </dependency>
   
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-web</artifactId>
       <version>${spring.version}</version>
   </dependency>
   
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-oxm</artifactId>
       <version>${spring.version}</version>
   </dependency>
   
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-tx</artifactId>
       <version>${spring.version}</version>
   </dependency>
   
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-jdbc</artifactId>
       <version>${spring.version}</version>
   </dependency>
   
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-webmvc</artifactId>
       <version>${spring.version}</version>
   </dependency>
   
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-aop</artifactId>
       <version>${spring.version}</version>
   </dependency>
   
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-context-support</artifactId>
       <version>${spring.version}</version>
   </dependency>
   
   <dependency>
       <groupId>org.springframework</groupId>
       <artifactId>spring-test</artifactId>
       <version>${spring.version}</version>
   </dependency>
   
   <!-- 日志文件管理包 -->
   <!-- log start -->
   <dependency>
       <groupId>log4j</groupId>
       <artifactId>log4j</artifactId>
       <version>${log4j.version}</version>
   </dependency>
   
   <dependency>
       <groupId>org.slf4j</groupId>
       <artifactId>slf4j-api</artifactId>
       <version>${slf4j.version}</version>
   </dependency>
   
   <dependency>
       <groupId>org.slf4j</groupId>
       <artifactId>slf4j-log4j12</artifactId>
       <version>${slf4j.version}</version>
   </dependency>
   ```

2. 创建类，在类里面创建方法

   ```java
   public class User {
       public void show() {
           System.out.println("user...");
       }
   }
   ```

3. 创建spring配置文件applicationContext.xml，建议放在src/main/resources下

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <beans xmlns="http://www.springframework.org/schema/beans"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xmlns:context="http://www.springframework.org/schema/context" xmlns:tx="http://www.springframework.org/schema/tx"
          xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd http://www.springframework.org/schema/context http://www.springframework.org/schema/context/spring-context.xsd http://www.springframework.org/schema/tx http://www.springframework.org/schema/tx/spring-tx.xsd">
   
   </beans>
   ```

4. 在spring配置文件中配置创建类

   ```xml
   <bean id="user" class="com.xmos.ssm.model.User"></bean>
   ```

5. 测试创建类

   ```java
   @Test
   public void test() {
       //加载spring配置文件，根据bean id创建对象
       ApplicationContext ctx = new ClassPathXmlApplicationContext("applicationContext.xml");
       //得到配置的对象
       User user = (User) ctx.getBean("user");
       user.show();
   }
   ```

## 5. Spring的bean管理（xml方式）

### 5.1 bean实例化的方式

- 概念：在spring里通过配置文件创建对象

- bean实例化的三种方式

  - 使用类的无参构造创建（见入门案例）

  - 使用静态工厂创建

    ```java
    public class UserFactory {
        public static User getUser() {
            return new User();
        }
    }
    ```

    ```xml
    <bean id="userFactory" class="com.xmos.ssm.model.UserFactory"></bean>
    <bean id="user" class="com.xmos.ssm.model.UserFactory" factory-method="getUser"></bean>
    ```

  - 使用实例工厂创建

    ```java
    public class UserFactory {
        public User getUser() {
            return new User();
        }
    }
    ```

    ```xml
    <bean id="userFactory" class="com.xmos.ssm.model.UserFactory"></bean>
    <bean id="user" class="com.xmos.ssm.model.UserFactory" factory-bean="userFactory" factory-method="getUser"></bean>
    ```

### 5.2 bean标签常用属性

- id：唯一标识bean，根据id值获取对象，不能包含特殊符号
- class：类的全路径
- name：功能和id一致，但可以包含特殊符号
- scope：
  - singleton：单例，默认值
  - prototype：多例
  - request：把创建的对象放到request域里面
  - session：把创建的对象放到session里面
  - globalSession：把创建的对象放到globalSession里面

## 6. 属性注入（xml方式）

- 概念：创建对象的时候，设置类的属性值
- spring属性注入的两种方式
  - set方法注入
  - 有参构造函数注入

### 6.1 注入方式

#### 6.1.1 set注入

```java
public class User {
    private String name;

    //set注入
    public void setName(String name) {
        this.name = name;
    }

    public void show() {
        System.out.println("user..." + name);
    }
}
```

```xml
<bean id="user" class="com.xmos.ssm.model.User">
	<property name="name" value="xmos"></property>
</bean>
```

#### 6.1.2 有参构造注入

```java
public class User {
    private String name;

    //有参构造注入
    public User(String name) {
        this.name = name;
    }

    public void show() {
        System.out.println("user..." + name);
    }
}
```

```xml
<bean id="user" class="com.xmos.ssm.model.User">
    <constructor-arg name="name" value="xmos"></constructor-arg>
</bean>
```

### 6.2 注入对象类型

1. 创建UserService和UserDao类

   ```java
   public class UserService {
       private UserDao userDao;
   
       public void setUserDao(UserDao userDao) {
           this.userDao = userDao;
       }
   
       public void add() {
           userDao.add();
       }
   }
   
   public class UserDao {
       public void add() {
           System.out.println("add...");
       }
   }
   ```

2. 通过配置文件在userService中注入userDao对象

   ```xml
   <bean id="userDao" class="com.xmos.dao.UserDao"></bean>
   <bean id="userService" class="com.xmos.service.UserService">
       <!--通过set方法注入userDao对象-->
       <property name="userDao" ref="userDao"></property>
   </bean>
   ```

### 6.3 注入复杂类型属性

- 数组

  ```xml
  <property name="arrs">
      <list>
          <value>小王</value>
          <value>小马</value>
          <value>小宋</value>
      </list>
  </property>
  ```

- list集合

  ```xml
  <property name="list">
      <list>
          <value>小奥</value>
          <value>小金</value>
          <value>小普</value>
      </list>			
  </property>
  ```

- map

  ```xml
  <property name="map">
      <map>
          <entry key="aa" value="lucy"></entry>
          <entry key="bb" value="mary"></entry>
          <entry key="cc" value="tom"></entry>
      </map>
  </property>
  ```

- properties类型

  ```xml
  <property name="properties">
      <props>
          <prop key="driverclass">com.mysql.jdbc.Driver</prop>
          <prop key="username">root</prop>
      </props>
  </property>
  ```

## 7. IoC和DI的区别

- IoC：控制反转，把对象的创建交给spring进行管理
- DI：依赖注入，设置对象的属性值
- 关系：**依赖注入不能单独存在，需要在IoC基础之上完成操作**

## 8. Spring整合web项目

- 整合前：在每个servlet中都会执行以下代码获取spring容器中的对象，重复代码多，效率低

  ```java
  ApplicationContext ctx = new ClassPathXmlApplicationContext("applicationContext.xml");
  User user = (User)ctx.getBean("user");
  ```

- 实现思想：把加载配置文件和创建对象过程放在服务器启动时候完成

- 实现原理

  - ServletContext
  - ServletContextListener（监听器）

- 具体过程

  1. 在服务器启动时候，为每个项目创建一个ServletContext对象

  2. 当监听器监听到ServletContext对象创建时候，加载spring配置文件

  3. 创建spring文件配置的类的对象

  4. 通过ServletContext.setAttribute()方法添加创建出的对象

  5. 通过ServletContext.getAttribute()获取创建的对象

     ```xml
     <!--指定监听器加载spring配置文件路径-->
     <context-param>
         <param-name>contextConfigLocation</param-name>
         <param-value>classpath:applicationContext.xml</param-value>
     </context-param>
     <!--配置监听器-->
     <listener>
         <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
     </listener>
     ```

## 9. Spring的bean管理（注解）

### 9.1 注解介绍

- 代码里面的特殊标记，可以完成某些功能
- 注解的写法：@注解名称(属性名=属性值)，只有属性值时，属性名默认是value属性
- 注解可以使用在类，方法和属性上面

### 9.2 注解创建对象

#### 9.2.1 步骤

1. spring配置文件中开启注解扫描

   ```xml
   <!--开启注解扫描，扫描包里面类、方法、属性上是否有注解-->
   <context:component-scan base-package="com.xmos.ssm"></context:component-scan>
   <!--扫描属性上的注解，有了上面就不用配置-->
   <!--<context:annotation-config></context:annotation-config>-->
   ```

2. 使用注解创建对象

   ```java
   @Component(value="user") //相当于<bean id="user" class=""></bean>
   public class User {}
   ```

3. 测试

   ```java
   @Test
   public void test() {
       ApplicationContext ctx = new ClassPathXmlApplicationContext("applicationContext.xml");
       User user = (User) ctx.getBean("user");
       user.show();
   }
   ```

#### 9.2.2 分析

1. 创建对象有四个注解，功能都一样
   - @Component
   - @Controller：WEB层
   - @Service：业务层
   - @Repository：持久层
2. 设置创建对象是单实例还是多实例
   - @Scope("singleton")：单例
   - @Scope("prototype")：多例

### 9.3 注解注入属性

1. @Autowired

   默认按类型装配（这个注解是属于spring的），默认情况下必须要求依赖对象必须存在，如果要允许null值，可以设置它的required属性为false，如：@Autowired(required=false) ，如果我们想使用名称装配可以结合@Qualifier注解进行使用

2. @Resource

   - 如果同时指定了name和type，则从Spring上下文中找到唯一匹配的bean进行装配，找不到则抛出异常

   - 如果指定了name，则从上下文中查找名称（id）匹配的bean进行装配，找不到则抛出异常

   - 如果指定了type，则从上下文中找到类型匹配的唯一bean进行装配，找不到或者找到多个，都会抛出异常

   - 如果既没有指定name，又没有指定type，则自动按照byName方式进行装配；如果没有匹配，则回退为一个原始类型进行匹配，如果匹配则自动装配；

## 10. AOP概念（未完）



## 11. Spring的声明式事务管理（注解）

1. 配置数据源

   ```XML
   <!--配置数据源-->
   <bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
       <property name="driverClassName" value="com.mysql.jdbc.Driver"></property>
       <property name="url" value="jdbc:mysql://localhost:3306/jdbc"></property>
       <property name="username" value="root"></property>
       <property name="password" value="123456"></property>
   </bean>
   ```

2. 配置事务管理器

   ```XML
   <!--配置事务管理器-->
   <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
       <!--注入dataSource-->
       <property name="dataSource" value="dataSource"></property>
   </bean>
   ```

3. 配置JdbcTemplate

   ```xml
   <!--配置JdbcTemplate-->
   <bean id="jdbcTemplate" class="org.springframework.jdbc.core.JdbcTemplate">
       <!--注入dataSource-->
       <property name="dataSource" ref="dataSource"></property>
   </bean>
   ```

4. 开启事务注解

   ```XML
   <!--开启事务注解-->
   <tx:annotation-driven transaction-manager="transactionManager"></tx:annotation-driven>
   ```

5. 在需要使用事务的方法或类上添加注解，遇到**运行时异常**自动回滚

   ```java
   @Transactional
   public void transferAccount() {
       String sql = "update user set amt=amt-1000 where name='tmos'";
       jdbcTemplate.update(sql);
       int i = 1/0;
       sql = "update user set amt=amt+1000 where name='xmos'";
       jdbcTemplate.update(sql);
   }
   ```