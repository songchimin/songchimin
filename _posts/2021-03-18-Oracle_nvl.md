---
layout: post
title: "Oracle NVL, NVL, COALESCE 내에 스칼라 서브쿼리 사용 팁"
categories:
  - Markup
tags:
  - Sql
  - Oracle
---

## NVL, NVL2, COALESCE 내에 스칼라 서브쿼리(SELECT문에 있는 서브쿼리) 사용시 문제

### Oracle
```SQL
  NVL("값", "지정값")
   : 값이 null인 경우 지정값을 출력한다.
  NVL2("값", "지정값1", "지정값2")
   : null이 아닌경우 지정값1을  출력하고, null인 경우 지정값2을 출력한다.
  DECODE()로 표현 가능
   : DECODE(COMM, null, 0, COMM)  --NVL
   : DECODE(COMM, null, "N", "Y") --NVL2
  COALESCE("값1", "값2", "값3"...)
   : 값1 부터 시작하여 null이 아닌 값을 출력한다.
```
### 팁
 - NVL의 두 번째 와 NVL2의 세 번재 인수에 스칼라 서브쿼리를 사용하면 무조건 수행 됨.
 - COALESCE 경우 값1에 서브쿼리가 NULL이 아닐경우 다음 인자들의 스칼라 서브쿼리가 실행 되지 않음.
