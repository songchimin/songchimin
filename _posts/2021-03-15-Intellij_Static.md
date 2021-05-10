---
layout: post
title: "Intellij 수정 사항 반영(서버 재시작 X)"
categories:
  - Markup
tags:
  - Java
  - Intellij
  - static
---

## static파일을 개발할때 서버를 재시작 하지 않고 수정한 내용이 반영 됨.

### application.yml
```java
  spring:
    devtools:
      livereload:
        enabled: true
      restart:
        enabled: false
    freemarker:
      cache: false
```