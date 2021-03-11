---
layout: post
title: "DECODE와 CASE"
categories:
  - Markup
tags:
  - SQL
  - QUERY
  - ORACLE
---

## DECODE와 CASE

```SQL

1. DECODE
DECODE(값, IF1, THEN1, IF2, THEN2, .... ) 

2. CASE 
CASE  
    WHEN IF조건1 THEN1
    WHEN IF조건2 THEN2
        ....
ELSE  
END

예) 값이 IF1 만족하면 첫번째, IF2 만족하면 두번째 ... 를 출력

**CASE는 STATEMENT 이고 DECODE는 함수**
**단순한 쿼리에서는 성능 차이가 없음**
**NULL과 NULL 비교 시 DECODE는 참, CASE는 거짓을 반환하므로 CASE문으로 NULL 비교 연산 시 쿼리 작성에 주의해야**
**DECODE는 등가연산만 가능하지만 CASE는 다양한 비교연산이 가능**


```