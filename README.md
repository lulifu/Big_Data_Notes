# Big_Data

Notes for BD

- [Big\_Data](#big_data)
  - [In progress](#in-progress)
  - [Growth Path 学习路径](#growth-path-学习路径)
    - [Coding](#coding)
    - [Java](#java)
    - [JavaWeb](#javaweb)
    - [SQL](#sql)
    - [Hadoop](#hadoop)
    - [Flink](#flink)
    - [SSM](#ssm)
    - [Distributed System](#distributed-system)
    - [Interview](#interview)
    - [To-do List](#to-do-list)
  - [Questions](#questions)

## In progress

- 项目文档
- Java Basic
- MySQL
- Maven, Git
- StarRocks
- LeetCode

## Growth Path 学习路径

### Coding

- 剑指offer
- Labuladong算法小炒
- 代码随想录 刷题

### Java

- 面向对象：封装、继承、多态、抽象类、接口
- 集合与泛型：Collection，Map，List，Set
- 文件操作：File，InputStream/OutputStream
- 进程线程：Thread、线程通信、线程安全synchronized
- 反射、类的加载机制
- Lambda表达式、函数式接口、StreamAPI
- MySQL：DML，DDL，DCL, DQL
- JDBC规范与实现：PreparedStatement, Druid连接池、封装BaseDAO

### JavaWeb

TBD

### SQL

- SQL 必知必会
- MySQL 必知必会

### Hadoop

- HDFS
- HBase
- Hive

### Flink

### SSM

- Maven 项目依赖管理
- Spring 容器框架
- SpringMVC Web框架
- MyBatis ORM框架
- Linux 服务器系统
- Redis 数据缓存框架
- SpringSecurity 权限框架

### Distributed System

- Git 版本控制与协同开发
- SpringBoot 一站式框架
- SpringCloud：Eureka 注册中心/配置中心 ｜ OpenFeign 声明式远程调用 ｜ Hystrix 服务熔断 ｜ Gateway 网关
- Docker 容器化
- Nginx 反向代理服务和负载均衡
- Elasticsearch 检索/分析
- RabbitMQ/Kafa 消息队列

参考：

在Java领域，SSM是指Spring、Spring MVC和MyBatis这三个开源框架的组合。这种组合因其强大的功能和灵活性而在Java企业级应用开发中广受欢迎。下面简要介绍这三个框架及其组合的优势：

1. **Spring**：
   - Spring是一个轻量级的控制反转（IoC）和面向切面编程（AOP）的容器框架。
   - 它通过DI（依赖注入）机制管理应用中的对象，并通过AOP支持声明式事务管理。
   - Spring提供了丰富的模块，如Spring Security、Spring JDBC、Spring Transaction Management等，用于简化企业级应用开发。

2. **Spring MVC**：
   - Spring MVC是基于Spring的一个MVC（Model-View-Controller）框架，用于构建Web应用程序。
   - 它提供了一种分离的方式来开发Web应用，通过Controller接收请求、更新Model，并返回View。

3. **MyBatis**：
   - MyBatis是一个半自动ORM（Object-Relational Mapping）框架。
   - 它提供了将数据库中的记录与Java对象之间的映射，而不需要编写大量的JDBC代码。
   - 通过MyBatis，开发者可以通过XML或注解的方式映射SQL语句，实现数据持久化。

SSM组合的优势：

- **松耦合**：Spring作为管理层，MyBatis作为持久层，Spring MVC作为表现层，三者结合在一起，可以构建出松耦合、易于维护的应用程序。
- **开发效率**：SSM组合提供了一套成熟的解决方案，能够大幅提高开发效率，尤其是对于复杂的业务逻辑和数据操作。
- **灵活性和可扩展性**：Spring的DI和AOP特性使得应用程序更加灵活，容易适应需求变化和扩展。
- **社区支持**：每个框架都有活跃的社区和丰富的文档资源，有利于解决开发过程中遇到的问题。

SSM框架组合是Java Web开发的经典选择，适用于各种规模的企业级应用。

### Interview

- Java 底层源码
- JUC 底层源码
- JVM 系统分析与调优
- MySQL 面试
- Spring 源码分析

### To-do List

- 开源经历
- Kaggle: Algorithms about Risk Control
- Hive
- Kafka
- Flink
- HBase
- 《大数据之路：阿里巴巴大数据实践》

日志收集框架：Flume、Logstash、Filebeat

分布式文件存储系统：Hadoop HDFS

数据库系统：Mongodb、HBase

分布式计算框架：

批处理框架：Hadoop MapReduce
流处理框架：Storm
混合处理框架：Spark、Flink
查询分析框架：Hive 、Spark SQL 、Flink SQL、 Pig、Phoenix

集群资源管理器：Hadoop YARN

分布式协调服务：Zookeeper

数据迁移工具：Sqoop

任务调度框架：Azkaban、Oozie

集群部署和监控：Ambari、Cloudera Manager

## Questions

- 必须要先学Hadoop才能学Hive和Spark吗？
