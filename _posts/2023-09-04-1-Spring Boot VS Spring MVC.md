---
layout: post
categories: 공부
title: 중요 Spring 개념
subtitle: 용어 정리
tags: [공부, 기타]
---

## <U> Spring Boot VS Spring MVC </U>

참고  
[https://www.udemy.com/course/spring-boot-and-spring-framework-korean/learn/lecture](https://www.udemy.com/course/spring-boot-and-spring-framework-korean/learn/lecture)

#### Spring Framework

 Spring Framework는 의존성을 주입하는 것이 전부이다. 의존성을 정의하고 의존성을 식별하여 자동으로 연결하는 것이다. 물론 @Component, @Service 등 다양한 주석을 사용하여 의존성을 정의할 수 있다.  
 의존성을 정의한 후에는 의존성을 식별(Scan)해야 한다. 여기서 컴포넌트 스캔이 사용된다. 특정 패키지에서 컴포넌트 스캔을 실행하여 해당 패키지에서 정의된 모든 컴포넌트를 식별할 수 있다.  
 모든 컴포넌트와 의존성을 식별하고 나면 이를 자동으로 연결(@AutoWired)할 수 있다. 이것들이 Spring Framework의 코드 작업이다. 하지만 의존성 주입만으로는 강력한 애플리케이션을 빌드할 수 없다. 다른 프레임워크가 필요하다. 만약 데이터베이스와 통신해야 한다면 Hibernate 또는 JPA가 필요할 것이고, 단위 테스트를 작성한다면 Junit과 Mockito가 필요할 것이다.  
 이를 위해 Spring Modules와 Spring Projects를 사용하여 Spring 생태계를 확장할 수 있고, 다른 프레임워크와 잘 통합할 수 있다. 데이터베이스와 통신하려는 경우 Spring을 통해 Hibernate JPA와 원활하게 통합할 수 있고, 단위 테스트를 작성하려는 경우에도 Spring을 통해 Junit Mockito와 잘 통합할 수 있다.

 **Spring Framework의 핵심**은 의존성 주입이고 Spring Modules와 Spring Projects는 Spring 생태계를 확장하여 다른 프레임워크와 쉽게 통합할 수 있도록 지원한다.

#### Spring MVC (Spring Module)

 그럼 Spring MVC는 무엇일까? Spring MVC는 Spring Module이다. **Spring MVC의 핵심**은 웹 애플리케이션과 REST API의 빌드 과정을 간소화하는 것이다. 즉, 웹 앱과 REST API에만 집중하는 것이다. Spring MVC가 사용되기 전에 가장 많이 사용된 프레임워크는 Struts였다. Struts를 사용해 웹 애플리케이션을 빌드하는 작업은 매우 복잡했고, 강한 결합(Tight Couple)이 많이 사용됐었다. 하지만 Spring MVC는 Struts보다 더 나은 웹 애플리케이션 빌드 방법을 제공한다. Spring MVC를 사용하면 @Controller, @RestController @RequestMapping과 같은 주석을 사용할 수 있다.  


#### Spring Boot

 정리하자면 Spring 프레임워크의 핵심은 의존성 주입이고, Spring MVC는 웹 애플리케이션과 REST API를 쉽게 빌드하도록 지원한다. Spring 프레임워크와 Spring MVC의 사용으로 여러 가지 설정을 pom.xml, web.xml, applicationcontext.xml에서 쉽게 관리할 수 있다.  
 Spring Boot는 Spring Project이며, 목표는 프로덕션 환경에 사용 가능한 **애플리케이션을 빠르게 빌드**하도록 지원하는 것이다. **Spring Boot의 주요 기능**은 Starter Projects와 Auto Configuration이다. 웹 애플리케이션을 개발하려는 경우 web starter가 **필요한 모든 의존성을 가져온다.** Auto Configuration을 사용하면 Spring Framework와 Spring MVC 등 다른 **프레임워크를 설정할 필요가 없다.** 또한 클래스 경로에 있는 항목에 따라 디폴트 설정을 자동으로 제공한다. 그리고 Spring Boot는 여러 가지 비기능 요구사항도 사용 설정할 수 있다. Embedded Server를 사용하여 애플리케이션의 배포 과정을 간소화할 수 있다. 게다가 Spring Boot는 actuator를 통해 endpoint를 제공하여 애플리케이션 모니터링, 디폴트 로깅과 오류 처리도 가능하며, Profile과 ConfigurationProperties를 통해 애플리케이션 설정을 간소화할 수 있다.

즉, Spring Boot는 Spring MVC와 Spring을 쉽게 사용할 수 있도록 하는 도구(wrapper)이다.
