---
layout: post
title: "JSTL Format"
categories:
  - Markup
tags:
#  - css
  - html
  - jsp
  - format
  - jstl
---

## JSTL Format을 이용한 날짜 계산.

### Source

Step1. 선언
```html
  <%@ taglib prefix = "fmt" uri = "http://java.sun.com/jsp/jstl/fmt" %>
```

<br>

Step2. `<fmt:parseDate>`를 이용하여 String >> Date 형 변환
```html
<fmt:parseDate>를 이용하여 String >> Date 형 변환

계산할 데이터 형태가 가공되지 않은 문자열 형태일 경우 많으므로 계산을 위해 DATE형으로 변환 시켜 줍니다.

<fmt:parseDate>태그를 이용하여 문자열로 이루어진 여러가지 포맷의 데이터를 DATE형으로 변환 시킬 수 있습니다.


Ex)

startDate = 2019-07-27
endDate = 2019-07-30
<fmt:parseDate var="startDate_D" value="${startDate }" pattern="yyyy-MM-dd"/>
<fmt:parseDate var="endDate_D" value="${endDate }" pattern="yyyy-MM-dd"/>


startTime = 0215
endTime = 0100
<fmt:parseDate var="startTime_D" value="${startTime }" pattern="HHmm"/>
<fmt:parseDate var="endTime_D" value="${endTime }" pattern="HHmm"/>

```

<br>

Step3. `<fmt:parseNumber>`를 이용하여 Date >> Number 변환
```html
Date타입의 두 변수를 계산하기 위하여 Number 타입으로 변경해 줍니다.
변경되는 단위는 밀리세컨드(ms) 입니다.

날짜는 타임스탬프를 기준으로 (1970-01-01 00:00:00) 계산됩니다.

1초 = 1,000 ms (1* 1000)
1분 = 60,000 ms (60 * 1000)
1시간 = 3,600,000 ( 60 * 60 * 1000 )
1일 = 86,400,000 ( 24 * 60 * 60 * 1000)

<fmt:parseNumber var="startTime_N" value="${startTime_D.time}" integerOnly="true" /> 
<fmt:parseNumber var="endTime_N" value="${endTime_D.time}" integerOnly="true"/>

소수점 버리기(현재시간과의 차이)
<fmt:formatNumber type="number" pattern="0.0" value="${ nowdate - strDate) / (endDate - strDate * 100}"/>
```
