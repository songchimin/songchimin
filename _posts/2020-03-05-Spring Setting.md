---
layout: post
title: "SpringFramework Setting"
categories:
  - Spring
tags:
  - Setting
---

## SpringBoot 설정.
```Java

Application.properties

server.port=8081

spring.mvc.view.prefix=/WEB-INF/views/
spring.mvc.view.suffix=.jsp
spring.resources.static-locations=file:///D:/finalProject/file/Image

### oracle set
spring.datasource.driver-class-name=oracle.jdbc.OracleDriver
#spring.datasource.url=jdbc:oracle:thin:@ ip :1521/xe
spring.datasource.url=jdbc:oracle:thin:@localhost:1521/	xe
spring.datasource.username=scott
spring.datasource.password=tiger

#mybatis
mybatis.mapper-locations=classpath:mybatis/mapper/**/**.xml

```




### build.gradle - dependencies

dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-jdbc'
	implementation 'org.springframework.boot:spring-boot-starter-web'
	implementation 'org.mybatis.spring.boot:mybatis-spring-boot-starter:2.1.1'
	compileOnly 'org.projectlombok:lombok'
	annotationProcessor 'org.projectlombok:lombok'
	providedRuntime 'org.springframework.boot:spring-boot-starter-tomcat'
	testImplementation('org.springframework.boot:spring-boot-starter-test') {
		exclude group: 'org.junit.vintage', module: 'junit-vintage-engine'
	}
	implementation 'javax.servlet:jstl'
  	implementation 'org.apache.tomcat.embed:tomcat-embed-jasper'
  	implementation 'org.bgee.log4jdbc-log4j2:log4jdbc-log4j2-jdbc4:1.16'
  	implementation 'com.google.firebase:firebase-admin:6.7.0'
}

