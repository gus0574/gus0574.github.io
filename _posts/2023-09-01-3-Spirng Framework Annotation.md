---
layout: post
categories: 공부
title: Spirng Framework Annotation
subtitle: 용어 정리
tags: [공부, 기타]
---

## <U> Spirng Framework Annotation </U>

참고  
[https://www.udemy.com/course/spring-boot-and-spring-framework-korean/learn/lecture][https://www.udemy.com/course/spring-boot-and-spring-framework-korean/learn/lecture]


#### @Configuration

@Configuration은 클래스가 @Bean 메서드를 하나 이상 선언함을 나타낸다. Spring 컨테이너에서 이것을 처리하여 Bean 정의를 생성한다. @Configuration을 추가하면 Java 설정 파일을 만든다는 것을 의미한다. Java 설정 파일에서는 메서드를 몇 개든 정의할 수 있고 이러한 메서드에 @Bean 어노테이션 추가할 수 있다. 그러면 메서드로 반환되는 모든 값에 Spring이 Bean을 자동으로 생성한다. @Configuration 클래스의 예를 들면, @Bean 어노테이션을 사용해 Bean의 수를 정의한다.

#### @ComponentScan

@ComponentScan은 컴포넌트를 스캔할 특정 패키지를 정의한다. Spring Framework에서는 모든 컴포넌트가 정의된 위치를 알아야 한다. 이것을 ComponentScan으로 처리한다. 이 어노테이션을 사용하면 컴포넌트를 스캔할 패키지를 지정할 수 있다. 패키지를 지정하지 않으면 이 어노테이션을 선언한 클래스의 패키지에서 스캔된다. 현재 패키지뿐만 아니라 하위 패키지에서도 컴포넌트를 스캔한다. 

#### @Component

@Component는 어노테이션한 클래스가 컴포넌트임을 나타낸다. @Component 클래스가 ComponentScan에 속한다면 Spring Bean이 생성된다.  
@Component의 스테레오 타입은 @Service, @Controller, @Repository 등이 있다.

#### @Service

@Service는 어노테이션한 클래스에 비즈니스 논리가 있음을 나타내는 @Component의 한 종류이다. 

#### @Controller

@Controller는 어노테이션한 클래스가 컨트롤러임을 나타내는 @Component의 한 종류이고 웹 컨트롤러를 예로 들 수 있다. 일반적으로 웹 애플리케이션과 REST API에서 컨트롤러를 정의하는 데 사용된다. 

#### @Repository

@Repository도 마찬가지로 @Component의 종류 중 하나이다. 어노테이션한 클래스가 데이터베이스에서 데이터를 검색하거나 조작하는 데 사용된다는 의미이다.

#### @Primary

@Primary는 여러 Bean이 단일 값 의존성에 자동 연결될 후보일 때 Bean에 우선순위를 부여해야 함을 나타낸다. 그러니 후보가 여러 개일 때 특정한 Bean에 우선순위를 두려면 Primary를 사용하면 된다.

#### @Qualifier

@Qualifier는 자동 연결 시 후보 Bean의 한정자(=특정문자 or 예약어)로 필드나 매개 변수에서 사용된다. @Primary는 아주 일반적이다. 우선순위를 지정할 뿐이다.  
@Qualifier는 아주 구체적이다. 모든 컴포넌트에 한정자를 추가할 수 있고 자동 연결(AutoWire) 시 한정자를 사용할 수 있다. 여기서 특정한 한정자로 Bean을 자동 연결하겠다고 작성할 수 있다.

#### @Lazy

Spring Bean은 일반적으로 컨텍스트가 실행되는 대로 즉시 초기화된다. 하지만 Bean을 지연 초기화하려 한다면 @Lazy 어노테이션을 사용하면 된다.

#### @Scope(value=“ConfigurableBeanFactory.SCOPE_PROTOTYPE)

특정 컴포넌트에 프로토타입 스코프를 정의할 수 있다. Bean을 프로토타입으로 정의한다. 이것은 Bean을 참조할 때마다 인스턴스가 새로 만들어진다는 뜻이다.  
단, 기본값은 싱글톤 타입이기 때문에 @Scope 어노테이션이 없거나, @Scope 어노테이션의 값을 SCOPE_SINGLETON으로 설정한 경우에는 싱글톤 타입이 되며 IoC 컨테이너에 특정 Bean의 인스턴스 하나씩만 주어진다. 싱글톤 스코프일 때는 Bean을 100번 참조하더라도 같은 인스턴스가 다시 사용된다.

#### @PostConstruct

의존성 주입이 수행된 이후 초기화를 위해 실행될 메서드를 나타낸다. 모든 의존성을 Bean에 주입한 후 초기화하려는 경우 또는 모든 의존성이 준비되는 대로 데이터베이스에서 몇 가지 값을 가져오려는 경우에 @PostConstruct를 사용하면 된다.

#### @PreDestroy

컨테이너에서 인스턴스를 삭제하는 과정을 거치고 있음을 알려주는 콜백 알림을 수신하는 메서드를 나타낸다. 보통 특정한 Bean에서 보유하고 있는 리소스를 해제하는 데 사용된다. 컨테이너나 Spring IoC 컨텍스트에서 Bean이 삭제되기 전에 @PreDestroy 어노테이션이 붙은 메서드를 호출한다. 리소스를 해제해야 하거나 정리해야 한다면 @PreDestroy 어노테이션이 붙은 메서드에 구현하는 게 좋다.

#### @Named

CDI, 즉 Contexts & Dependency Injection에서 다뤄진다. Spring에서 CDI 어노테이션을 구현하는 규격이다. @Named는 CDI 어노테이션이며 @Component과 유사하다.

#### @Inject

CDI 어노테이션으로 @Autowired와 아주 비슷하다. 