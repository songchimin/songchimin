---
layout: post
title: "Apache_Tomcat"
categories:
  - Markup
tags:
  - apache
  - tomcat
  - spring
  - info
---

## Apache_Tomcat.

1. 아파치 (Apache)

아파치 소프트웨어 재단의 오픈소스 프로젝트이다. 일명 웹서버로 불리며, 클라이언트 요청이 왔을때만 응답하는 정적 웹페이지에 사용된다.

웹서버 = 80번 포트로 클라이언트 요청(POST,GET,DELETE)이 왔을때만 응답함.

정적인 데이터만 처리한다.(HTML,CSS,이미지 등).



2. 톰캣 (Tomcat)

dynamic(동적)인 웹을 만들기 위한 웹 컨테이너, 서블릿 컨테이너라고 불리며, 웹서버에서 정적으로 처리해야할 데이터를 제외한 JSP, ASP, PHP 등은 웹 컨테이너(톰캣)에게 전달한다.

WAS(Web Application Server)
컨테이너, 웹 컨테이너, 서블릿 컨테이너라고 부름
JSP,서블릿처리,HTTP요청 수신 및 응답
아파치만 쓰면 정적인 웹페이지만 처리하므로 처리속도가 매우 빠르고 안정적이다.
하지만 톰캣(WAS)를 쓰면 동적인 데이터 처리가 가능하다. DB연결,데이터 조작, 다른 응용프로그램과 상호 작용이 가능하다. 톰캣은 8080포트로 처리한다.


3. 아파치톰캣 (Apache+Tomcat)

톰캣이 아파치의 기능 일부를 가져와서 제공해주는 형태이기 때문에 같이 합쳐서 부른다. WAS(Web Application Server)

<a href="{{ site.url }}/images/apache_tomecat.png"><img src="{{ site.url }}/images/apache_tomecat.png" alt="hashmap"></a>  
<center><b>[ 그림을 통해서 아파치와 톰캣의 차이를 알 수 있다. 톰캣은 일반적으로 WAS(Wep)라고 불리며, 톰캣은 아파치와 합쳐서 아파치톰캣 이라 부른다. ]</b></center><br>


아파치만 사용하면 정적인 웹페이지만 처리 가능

톰캣만 사용하면 동적인 웹페이지 처리가 가능하지만 아파치에서 필요한 기능을 못가져옴. 또한 여러 사용자가 요청할시에 톰캣에 과부하가 걸림.

아파치와 톰캣을 같이 쓰면 아파치는 정적인 데이터만 처리하고, JSP 처리는 Web Container(톰캣의 일부)로 보내주어 분산처리 할 수 있다.

아파치 : 80포트
톰캣 : 8080포트
(하지만 실제로는 80포트로 다 처리하므로, 8080포트는 아파치가 알아서 보내줌. 8080포트를 다루거나 보려면 리눅스단에서 처리하거나 수동적으로 포트 처리할때 빼고는 보기힘듬)



4. 아파치 톰캣 정리

<a href="{{ site.url }}/images/apache_tomecat_ab.png"><img src="{{ site.url }}/images/apache_tomecat_ab.png" alt="hashmap"></a>  
<center><b>[ 장단점 ]</b></center><br>
