---
layout: post
Title: "SpringBoot学习(一)、SpringBoot基本配置"
Date: 2020-05-02 16:06:34.00000000 + 09:00
---

# SpringBoot的基本配置

*默认大家已经是会新建SpringBoot项目(idea新建或者通过[https://start.spring.io/]*

[https://start.spring.io/]:https://start.spring.io/

## 定制Banner

**SpringBoot项目在启动的时候会有一个默认的启动图案：**

``` java
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.2.6.RELEASE)
```

我们可以把这个图案修改为我们自己想要的。在src/main/sources目录下心间banner.txt文件，然后讲自己的图案粘贴进去即可。ASCII图案可以通过网站一键生成，比如输入“s y b x” 生成图案后复制到banner.txt启动项目，控制台输出如下：

```java
/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/bin/java -XX:TieredStopAtLevel=1 -noverify -Dspring.output.ansi.enabled=always -Dcom.sun.management.jmxremote -Dspring.jmx.enabled=true -Dspring.liveBeansView.mbeanDomain -Dspring.application.admin.enabled=true -javaagent:/Applications/IntelliJ IDEA.app/Contents/lib/idea_rt.jar=53970:/Applications/IntelliJ IDEA.app/Contents/bin -Dfile.encoding=UTF-8 -classpath /Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/charsets.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/deploy.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/ext/cldrdata.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/ext/dnsns.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/ext/jaccess.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/ext/jfxrt.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/ext/localedata.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/ext/nashorn.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/ext/sunec.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/ext/sunjce_provider.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/ext/sunpkcs11.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/ext/zipfs.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/javaws.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/jce.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/jfr.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/jfxswt.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/jsse.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/management-agent.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/plugin.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/resources.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/jre/lib/rt.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/lib/ant-javafx.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/lib/dt.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/lib/javafx-mx.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/lib/jconsole.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/lib/packager.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/lib/sa-jdi.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_241.jdk/Contents/Home/lib/tools.jar:/Users/yuanzhipeng/idea/SpringBoot-yzp/springboot-yzp/target/classes:/Users/yuanzhipeng/.m2/repository/org/springframework/boot/spring-boot-starter-web/2.2.6.RELEASE/spring-boot-starter-web-2.2.6.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/boot/spring-boot-starter/2.2.6.RELEASE/spring-boot-starter-2.2.6.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/boot/spring-boot/2.2.6.RELEASE/spring-boot-2.2.6.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/boot/spring-boot-autoconfigure/2.2.6.RELEASE/spring-boot-autoconfigure-2.2.6.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/boot/spring-boot-starter-logging/2.2.6.RELEASE/spring-boot-starter-logging-2.2.6.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/ch/qos/logback/logback-classic/1.2.3/logback-classic-1.2.3.jar:/Users/yuanzhipeng/.m2/repository/ch/qos/logback/logback-core/1.2.3/logback-core-1.2.3.jar:/Users/yuanzhipeng/.m2/repository/org/apache/logging/log4j/log4j-to-slf4j/2.12.1/log4j-to-slf4j-2.12.1.jar:/Users/yuanzhipeng/.m2/repository/org/apache/logging/log4j/log4j-api/2.12.1/log4j-api-2.12.1.jar:/Users/yuanzhipeng/.m2/repository/org/slf4j/jul-to-slf4j/1.7.30/jul-to-slf4j-1.7.30.jar:/Users/yuanzhipeng/.m2/repository/jakarta/annotation/jakarta.annotation-api/1.3.5/jakarta.annotation-api-1.3.5.jar:/Users/yuanzhipeng/.m2/repository/org/yaml/snakeyaml/1.25/snakeyaml-1.25.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/boot/spring-boot-starter-json/2.2.6.RELEASE/spring-boot-starter-json-2.2.6.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/com/fasterxml/jackson/core/jackson-databind/2.10.3/jackson-databind-2.10.3.jar:/Users/yuanzhipeng/.m2/repository/com/fasterxml/jackson/core/jackson-annotations/2.10.3/jackson-annotations-2.10.3.jar:/Users/yuanzhipeng/.m2/repository/com/fasterxml/jackson/core/jackson-core/2.10.3/jackson-core-2.10.3.jar:/Users/yuanzhipeng/.m2/repository/com/fasterxml/jackson/datatype/jackson-datatype-jdk8/2.10.3/jackson-datatype-jdk8-2.10.3.jar:/Users/yuanzhipeng/.m2/repository/com/fasterxml/jackson/datatype/jackson-datatype-jsr310/2.10.3/jackson-datatype-jsr310-2.10.3.jar:/Users/yuanzhipeng/.m2/repository/com/fasterxml/jackson/module/jackson-module-parameter-names/2.10.3/jackson-module-parameter-names-2.10.3.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/boot/spring-boot-starter-tomcat/2.2.6.RELEASE/spring-boot-starter-tomcat-2.2.6.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/apache/tomcat/embed/tomcat-embed-core/9.0.33/tomcat-embed-core-9.0.33.jar:/Users/yuanzhipeng/.m2/repository/org/apache/tomcat/embed/tomcat-embed-el/9.0.33/tomcat-embed-el-9.0.33.jar:/Users/yuanzhipeng/.m2/repository/org/apache/tomcat/embed/tomcat-embed-websocket/9.0.33/tomcat-embed-websocket-9.0.33.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/boot/spring-boot-starter-validation/2.2.6.RELEASE/spring-boot-starter-validation-2.2.6.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/jakarta/validation/jakarta.validation-api/2.0.2/jakarta.validation-api-2.0.2.jar:/Users/yuanzhipeng/.m2/repository/org/hibernate/validator/hibernate-validator/6.0.18.Final/hibernate-validator-6.0.18.Final.jar:/Users/yuanzhipeng/.m2/repository/org/jboss/logging/jboss-logging/3.4.1.Final/jboss-logging-3.4.1.Final.jar:/Users/yuanzhipeng/.m2/repository/com/fasterxml/classmate/1.5.1/classmate-1.5.1.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/spring-web/5.2.5.RELEASE/spring-web-5.2.5.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/spring-beans/5.2.5.RELEASE/spring-beans-5.2.5.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/spring-webmvc/5.2.5.RELEASE/spring-webmvc-5.2.5.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/spring-aop/5.2.5.RELEASE/spring-aop-5.2.5.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/spring-context/5.2.5.RELEASE/spring-context-5.2.5.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/spring-expression/5.2.5.RELEASE/spring-expression-5.2.5.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/slf4j/slf4j-api/1.7.30/slf4j-api-1.7.30.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/spring-core/5.2.5.RELEASE/spring-core-5.2.5.RELEASE.jar:/Users/yuanzhipeng/.m2/repository/org/springframework/spring-jcl/5.2.5.RELEASE/spring-jcl-5.2.5.RELEASE.jar com.springboot.yzp.SpringbootYzpApplication
               __
              /\ \
  ____  __  __\ \ \____  __  _
 /',__\/\ \/\ \\ \ '__`\/\ \/'\
/\__, `\ \ \_\ \\ \ \L\ \/>  </
\/\____/\/`____ \\ \_,__//\_/\_\
 \/___/  `/___/> \\/___/ \//\/_/
            /\___/
            \/__/               
2020-05-02 18:31:17.372  INFO 58694 --- [           main] c.s.yzp.SpringbootYzpApplication         : Starting SpringbootYzpApplication on yuanzhipengdeMacBook-Pro-2.local with PID 58694 (/Users/yuanzhipeng/idea/SpringBoot-yzp/springboot-yzp/target/classes started by yuanzhipeng in /Users/yuanzhipeng/idea/SpringBoot-yzp)
2020-05-02 18:31:17.375  INFO 58694 --- [           main] c.s.yzp.SpringbootYzpApplication         : No active profile set, falling back to default profiles: default
2020-05-02 18:31:18.169  INFO 58694 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port(s): 8080 (http)
2020-05-02 18:31:18.186  INFO 58694 --- [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2020-05-02 18:31:18.187  INFO 58694 --- [           main] org.apache.catalina.core.StandardEngine  : Starting Servlet engine: [Apache Tomcat/9.0.33]
2020-05-02 18:31:18.256  INFO 58694 --- [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2020-05-02 18:31:18.257  INFO 58694 --- [           main] o.s.web.context.ContextLoader            : Root WebApplicationContext: initialization completed in 842 ms
2020-05-02 18:31:18.442  INFO 58694 --- [           main] o.s.s.concurrent.ThreadPoolTaskExecutor  : Initializing ExecutorService 'applicationTaskExecutor'
2020-05-02 18:31:18.655  INFO 58694 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8080 (http) with context path ''
2020-05-02 18:31:18.659  INFO 58694 --- [           main] c.s.yzp.SpringbootYzpApplication         : Started SpringbootYzpApplication in 1.584 seconds (JVM running for 2.083)
```

banner也可以关闭，在mian方法中：

```java
package com.springboot.yzp;

import org.springframework.boot.Banner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class SpringbootYzpApplication {

    public static void main(String[] args) {
        SpringApplication app = new SpringApplication(SpringbootYzpApplication.class);
        app.setBannerMode(Banner.Mode.OFF);
        app.run(args);
    }

}
```

## 全局配置文件

在src/main/sources目录下，SpringBoot提供了一个名为application.properties的全局配置文件，可对一些默认配置进行修改

`附件：`[application.properties中可配置所有官方属性](https://docs.spring.io/spring-boot/docs/current/reference/html/common-application-properties.html)

## 使用xml配置

虽然Spring Boot并不推荐我们继续使用xml配置，但如果出现不得不使用xml配置的情况，Spring Boot允许我们在入口类里通过注解`@ImportResource({"classpath:some-application.xml"})`来引入xml配置文件。

## Profile配置

Profile用来针对不同的环境下使用不同的配置文件，多环境配置文件必须以`application-{profile}.properties`的格式命，其中`{profile}`为环境标识。比如定义两个配置文件：

* application-dev.properties：测试环境：

`server.port=8081`

* application-prod.properties：生产环境：

`server.port=80812

至于哪个具体的配置文件会被加载，需要在application.properties文件中通过`spring.profiles.active`属性来设置，其值对应`{profile}`值。

如：`spring.profiles.active=dev`就会加载application-dev.properties配置文件内容。可以在运行jar文件的时候使用命令`java -jar xxx.jar --spring.profiles.active={profile}`切换不同的环境配置。