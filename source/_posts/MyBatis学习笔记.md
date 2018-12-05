---
title: MyBatis学习笔记
date: 2018-12-05 15:54:16
tags: 学习笔记
---

# MyBatis学习笔记

## 1. 对原生态jdbc程序开发中的问题的总结

### 1.1 环境

- jdk 1.8
- idea
- mysql 8

### 1.2 创建mysql相关库表数据

1. 执行以下建表语句：

   ```mysql
   CREATE TABLE `items` (
       `id` int(11) NOT NULL AUTO_INCREMENT,
       `name` varchar(32) NOT NULL COMMENT '商品名称',
       `price` float(10,1) NOT NULL COMMENT '商品定价',
       `detail` text COMMENT '商品描述',
       `pic` varchar(64) DEFAULT NULL COMMENT '商品图片',
       `createtime` datetime NOT NULL COMMENT '生产日期',
       PRIMARY KEY (`id`)
   );
   
   CREATE TABLE `orderdetail` (
       `id` int(11) NOT NULL AUTO_INCREMENT,
       `orders_id` int(11) NOT NULL COMMENT '订单id',
       `items_id` int(11) NOT NULL COMMENT '商品id',
       `items_num` int(11) DEFAULT NULL COMMENT '商品购买数量',
       PRIMARY KEY (`id`),
       KEY `FK_orderdetail_1` (`orders_id`),
       KEY `FK_orderdetail_2` (`items_id`),
       CONSTRAINT `FK_orderdetail_1` FOREIGN KEY (`orders_id`) REFERENCES `orders` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION,
       CONSTRAINT `FK_orderdetail_2` FOREIGN KEY (`items_id`) REFERENCES `items` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION
   );
   
   CREATE TABLE `orders` (
       `id` int(11) NOT NULL AUTO_INCREMENT,
       `user_id` int(11) NOT NULL COMMENT '下单用户id',
       `number` varchar(32) NOT NULL COMMENT '订单号',
       `createtime` datetime NOT NULL COMMENT '创建订单时间',
       `note` varchar(100) DEFAULT NULL COMMENT '备注',
       PRIMARY KEY (`id`),
       KEY `FK_orders_1` (`user_id`),
       CONSTRAINT `FK_orders_id` FOREIGN KEY (`user_id`) REFERENCES `user` (`id`) ON DELETE NO ACTION ON UPDATE NO ACTION
   );
   
   CREATE TABLE `user` (
       `id` int(11) NOT NULL AUTO_INCREMENT,
       `username` varchar(32) NOT NULL COMMENT '用户名称',
       `birthday` date DEFAULT NULL COMMENT '生日',
       `sex` char(1) DEFAULT NULL COMMENT '性别',
       `address` varchar(256) DEFAULT NULL COMMENT '地址',
       PRIMARY KEY (`id`)
   );
   
   ```

2. 执行以下初始化数据脚本：

   ```mysql
   insert  into `items`(`id`,`name`,`price`,`detail`,`pic`,`createtime`) values (1,'台式机',3000.0,'该电脑质量非常好！！！！',NULL,'2015-02-03 13:22:53'),(2,'笔记本',6000.0,'笔记本性能好，质量好！！！！！',NULL,'2015-02-09 13:22:57'),(3,'背包',200.0,'名牌背包，容量大质量好！！！！',NULL,'2015-02-06 13:23:02');
   
   insert  into `orders`(`id`,`user_id`,`number`,`createtime`,`note`) values (3,1,'1000010','2015-02-04 13:22:35',NULL),(4,1,'1000011','2015-02-03 13:22:41',NULL),(5,10,'1000012','2015-02-12 16:13:23',NULL);
   
   insert  into `user`(`id`,`username`,`birthday`,`sex`,`address`) values (1,'王五',NULL,'2',NULL),(10,'张三','2014-07-10','1','北京市'),(16,'张小明',NULL,'1','河南郑州'),(22,'陈小明',NULL,'1','河南郑州'),(24,'张三丰',NULL,'1','河南郑州'),(25,'陈小明',NULL,'1','河南郑州'),(26,'王五',NULL,NULL,NULL);
   ```

### 1.3 jdbc程序

### 1.4 问题总结

- 数据库连接，使用时就创建，不使用立即释放，对数据库进行频繁连接开启和关闭，造成数据库资源浪费，影响数据库性能。

  设想：使用数据库连接池管理数据库连接。

- 将sql语句硬编码到java代码中，如果sql 语句修改，需要重新编译java代码，不利于系统维护。

  设想：将sql语句配置在xml配置文件中，即使sql变化，不需要对java代码进行重新编译。

- 向preparedStatement中设置参数，对占位符号位置和设置参数值，硬编码在java代码中，不利于系统维护。

  设想：将sql语句及占位符号和参数全部配置在xml中。

- 从resultSet中遍历结果集数据时，存在硬编码，将获取表的字段进行硬编码，，不利于系统维护。

  设想：将查询的结果集，自动映射成java对象。

## 2. MyBatis框架

### 2.1 mybatis是什么？

mybatis是一个持久层的框架，是apache下的顶级项目。

mybatis托管到goolecode下，再后来托管到github下(https://github.com/mybatis/mybatis-3/releases)。

mybatis让程序员将主要精力放在sql上，通过mybatis提供的映射方式，自由灵活生成（半自动化，大部分需要程序员编写sql）满足需要sql语句。

mybatis可以将向 preparedStatement中输入的参数自动进行输入映射，将查询结果集灵活映射成java对象（输出映射）。

### 2.2 mybatis框架结构

![img](file:///C:/Users/Xmoss/AppData/Local/Temp/msohtmlclip1/01/clip_image001.gif)

## 3. 入门程序

### 3.1 环境

- jdk 1.8
- idea
- mysql 8.0.13
- mybatis-3.4.0.jar

### 3.2 log4j.properties

```prop
### direct log messages to stdout ###
log4j.appender.stdout=org.apache.log4j.ConsoleAppender
log4j.appender.stdout.Target=System.err
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=%d{ABSOLUTE} %5p %c{1}:%L - %m%n

### direct messages to file mylog.log ###
log4j.appender.file=org.apache.log4j.FileAppender
#log4j.appender.file.File=c:\mylog.log
log4j.appender.file.layout=org.apache.log4j.PatternLayout
log4j.appender.file.layout.ConversionPattern=%d{ABSOLUTE} %5p %c{1}:%L - %m%n

### set log levels - for more verbose logging change 'info' to 'debug' ###

log4j.rootLogger=debug, stdout
```

### 3.3 SqlMapConfig.xml

配置mybatis的运行环境，数据源、事务等。

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <!-- 加载属性文件 -->
    <properties resource="jdbc.properties">
        <!--properties中还可以配置一些属性名和属性值  -->
        <!-- <property name="jdbc.driver" value=""/> -->
    </properties>
    <!-- 和spring整合后 environments配置将废除-->
    <environments default="development">
        <environment id="development">
            <!-- 使用jdbc事务管理，事务控制由mybatis-->
            <transactionManager type="JDBC"/>
            <!-- 数据库连接池，由mybatis管理-->
            <dataSource type="POOLED">
                <property name="driver" value="${jdbc.driver}"/>
                <property name="url" value="${jdbc.url}"/>
                <property name="username" value="${jdbc.username}"/>
                <property name="password" value="${jdbc.password}"/>
            </dataSource>
        </environment>
    </environments>
</configuration>
```

### 3.4 jdbc.properties

```properties
jdbc.driver=com.mysql.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/jdbc
jdbc.username=root
jdbc.password=941218
```

### 3.5 根据用户id（主键）查询用户信息

#### 3.5.1 创建dao类

```java
public class User {
    //属性名和数据库表的字段对应
    private int id;
    private String username;//用户名
    private String sex;//性别
    private Date birthday;//生日
    private String address;//地址
}
```