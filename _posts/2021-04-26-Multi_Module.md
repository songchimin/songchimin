---
layout: post
title: "Intellij에서 Spring Boot Multi-Moudle(Gradle) 만들기"
categories:
  - Markup
tags:
  - Java
  - Springboot
  - Intellij
  - Gradle
---

# Intellij에서 Spring Boot Multi-Moudle(Gradle) 만들기

### Root 프로젝트 생성
<a href="{{ site.url }}/images/multi_module1.png"><img src="{{ site.url }}/images/multi_module1.png" alt="hashmap"></a>  


### 모듈 생성
<a href="{{ site.url }}/images/multi_module2.png"><img src="{{ site.url }}/images/multi_module2.png" alt="hashmap"></a>  


### 모듈 추가된 후 프로젝트 구조
<a href="{{ site.url }}/images/multi_module3.png"><img src="{{ site.url }}/images/multi_module3.png" alt="hashmap"></a>  


### 모듈 추가된 후 프로젝트 구조
- root 프로젝트의 build 디렉터와 src 폴더는 필요없으므로 삭제.
- stting.gradle에 신규 생성한 모듈의 내용 추가(자동)
- build.gradle에 모듈별 설정 추가

### settings.gradle
```java

rootProject.name = 'Gmemo'
include 'webapp'
include 'common'
include 'auth'
include 'core'

```

### build.gradle
```java

plugins {
    id 'org.springframework.boot' version '2.4.5'
    id 'io.spring.dependency-management' version '1.0.11.RELEASE'
    id 'java'
}

repositories {
    mavenCentral()
}

//subprojects 는 추가될 모듈둘에 공통적으로 적용될 내용들이 기술되어 있다.
subprojects {
    apply plugin: 'java'
    apply plugin: 'org.springframework.boot'
    apply plugin: 'io.spring.dependency-management'

    group = 'com.gmemo'
    version = '0.0.1-SNAPSHOT'
    sourceCompatibility = '1.8'

    repositories {
        mavenCentral()
    }

    dependencies {
        implementation 'org.springframework.boot:spring-boot-starter-thymeleaf'
        implementation 'org.springframework.boot:spring-boot-starter-web'
        implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
        developmentOnly 'org.springframework.boot:spring-boot-devtools'
        runtimeOnly 'com.h2database:h2'
        compileOnly('org.projectlombok:lombok')
        annotationProcessor 'org.projectlombok:lombok'
        testImplementation 'org.springframework.boot:spring-boot-starter-test'
        testImplementation('org.springframework.boot:spring-boot-starter-test'){
            exclude group: 'org.junit.vintage', module:'junit-vintage-engine'
        }
    }

    test {
        useJUnitPlatform()
    }
}

project(':webapp'){
    dependencies{
//        implementation project(':common')
        compile project(':common')
//        compile project(':auth')
    }
}
project(':common'){
    bootJar{
        enabled = false
    }
    jar {
        enabled = true
    }
    dependencies{
    }
}
project(':auth'){
    dependencies{
    }
}

project(':core'){
    dependencies{
    }
}

```


### module의 build.gradle 수정
```java

plugins {
    id 'java'
}

//독립 모듈
bootJar{
    enabled = false
}
jar {
    enabled = true
}

version 'unspecified'

repositories {
    mavenCentral()
}

dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.7.0'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.7.0'
}

test {
    useJUnitPlatform()
}

```


## Application 작성
모듈별로 서버를 구동해야 하므로 모듈별로 root에 패키지를 생성하고
Spring Boot Application 작성
<a href="{{ site.url }}/images/multi_module4.png"><img src="{{ site.url }}/images/multi_module4.png" alt="hashmap"></a>  