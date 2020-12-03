---
layout: post
Title: "SpringBoot学习(二)、引入mybatis框架"
Date: 2020-05-02 17:06:34.00000000 + 09:00
---

# SpringBoot 引入MyBatis

整合MyBatis之前，先搭建一个基本的SpringBoot项目，[springBoot基本配置]([http://sybx.cc/2020/05/SpringBoot%E5%AD%A6%E4%B9%A0(%E4%B8%80)/](http://sybx.cc/2020/05/SpringBoot学习(一)/)。然后引入mybatis-spring-boot-start和数据连接驱动(MySQL:5.7)

```java
        <!-- 引入mybatis框架 -->
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>1.3.1</version>
        </dependency>

        <!-- 引入mysql驱动 -->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <scope>runtime</scope>
        </dependency>
```

## Druid数据源

Druid是一个关系型数据库连接池，是阿里巴巴的一个开源项目，地址：https://github.com/alibaba/druid。Druid不但提供连接池的功能，还提供监控功能，可以实时查看数据库连接池和SQL查询的工作情况。

配置Druid：

* 引入Druid

```java
        <!-- 引入Druid -->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>druid-spring-boot-starter</artifactId>
            <version>1.1.10</version>
        </dependency>
```

* 配置文件

mybatis starter的隐性依赖发现，Spring Boot的数据源配置的默认类型是`org.apache.tomcat.jdbc.pool.Datasource`，为了使用Druid连接池，需要在application.properties下配置:

```java
## 测试环境 dev profile
server:
  port: 8081
  servlet:
    context-path: /web

## Druid 配置
spring:
  datasource:
    druid:
      ## 数据库访问配置,使用druid数据源
      type: com.alibaba.druid.pool.DruidDataSource
      driver-class-name: com.mysql.jdbc.Driver
      url: jdbc:mysql://127.0.0.1:3306/operaton?useUnicode=true&characterEncoding=UTF-8&allowMultiQueries=true&autoReconnect=true&failOverReadOnly=false
      username: root
      password: 123456
      # 连接池配置
      initial-size: 5
      min-idle: 5
      max-active: 20
      # 连接等待超时时间
      max-wait: 30000
      # 配置检测可以关闭的空闲连接间隔时间
      time-between-eviction-runs-millis: 60000
      # 配置连接在池中的最小生存时间
      min-evictable-idle-time-millis: 300000
      validation-query: select '1' from dual
      test-while-idle: true
      test-on-borrow: false
      test-on-return: false
      # 打开PSCache，并且指定每个连接上PSCache的大小
      pool-prepared-statements: true
      max-open-prepared-statements: 20
      max-pool-prepared-statement-per-connection-size: 20
      # 配置监控统计拦截的filters, 去掉后监控界面sql无法统计, 'wall'用于防火墙
      filters: stat,wall
      # Spring监控AOP切入点，如x.y.z.service.*,配置多个英文逗号分隔
      aop-patterns: com.springboot.yzp.servie.*

      # WebStatFilter配置
      web-stat-filter:
        enabled: true
        # 添加过滤规则
        url-pattern: /*
        # 忽略过滤的格式
        exclusions: '*.js,*.gif,*.jpg,*.png,*.css,*.ico,/druid/*'

      # StatViewServlet配置
      stat-view-servlet:
        enabled: true
        # 访问路径为/druid时，跳转到StatViewServlet
        url-pattern: /druid/*
        # 是否能够重置数据
        reset-enable: false
        # 需要账号密码才能访问控制台
        login-username: sybx
        login-password: sybx123
        # IP白名单
        # allow: 127.0.0.1
        #　IP黑名单（共同存在时，deny优先于allow）
        # deny: 192.168.31.149

      # 配置StatFilter
      filter:
        stat:
          log-slow-sql: true
```

上述配置不但配置了Druid作为连接池，而且还开启了Druid的监控功能。 其他配置可参考官方wiki——https://github.com/alibaba/druid/tree/master/druid-spring-boot-starter

此时，运行项目，访问http://localhost:8081/web/druid

![截屏2020-05-02 下午8.56.21](./截屏2020-05-02 下午8.56.21.png)

输入账号密码即可登陆Druid监控后台：

![截屏2020-05-02 下午8.56.30](./截屏2020-05-02 下午8.56.30.png)

关于Druid的更多说明，可查看官方wiki——[https://github.com/alibaba/druid/wiki/%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98](https://github.com/alibaba/druid/wiki/常见问题)

## 

使用MyBatis

接下来创建 entity、mapper、service、controller、db-sql

可以在Druid的控制台上查看SQL监情况；

![截屏2020-05-02 下午8.56.30](截屏2020-05-02 下午8.56.30.png)

```java
Source：https://github.com/yuanzhipeng/SpringBoot-yzp
```

