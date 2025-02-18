---
title: "Spring 개념 - DI (Dependency Injection)"
date: 2023-01-07
tags: ["Java", "Spring"]
---

### 의존 주입 (DI : Dependency Injection)을 하는 방법

1. Assembler라는 별도의 클래스 생성

   ```java
   public class Assembler {
       private MemberDao memberDao;
       private MemberRegisterService regSvc;

       public Assembler() {
           memberDao = new MemberDao();
           regSvc = new MemberRegisterService(memberDao);
       }

       public MemberDao getMemberDao() {
           return memberDao;
       }

       public MemberRegisterService getMemberRegisterService() {
           return regSvc;
       }
   }
   ```

2. Spring에서 지원하는 DI 사용
   ```java
   @Configuration
   public class AppCtx {
       @Bean
       public MemberDao memberDao() {
           return new MemberDao();
       }
       @Bean
       public MemberRegisterService memberRegSvc() {
           return new MemberRegisterService(memberDao());
       }
   }
   ```

### DI 방식

1. Constructor 방식
   ```java
   @Bean
       public MemberListPrinter listPrinter() {
           return new MemberListPrinter(memberDao(), memberPrinter());
       }
   ```
2. Setter method 방식
   ```java
   @Bean
   public MemberInfoPrinter infoPrinter() {
   	MemberInfoPrinter infoPrinter = new MemberInfoPrinter();
   	infoPrinter.setMemberDao(memberDao());
   	infoPrinter.setPrinter(memberPrinter());
   	return infoPrinter;
   }
   ```

- constructor 방식이 훨씬 깔끔해보인다.
- java bean에서는 getter와 setter를 이용해서 property를 정의한다고 한다.

### 두 개 이상의 Configuration 파일 사용 : @Autowired 활용

- AppConf1.java

  ```java
  @Configuration
  public class AppConf1 {
  	...
  }
  ```

  - AppConf2.java

  ```java
  import org.springframework.beans.factory.annotation.Autowired;

  @Configuration
  public class AppConf2 {
  	@Autowired
  	private MemberDao memberDao;
  	@Autowired
  	private MemberPrinter memberPrinter;

  	...
  }
  ```

- MainForSpring.java

  ```java
  ctx = new AnnotationConfigApplicationContext(AppConf1.class, AppConf2.class);
  ```

- Autowired annotation을 통해 다른 설정 파일의 객체를 가져올 수 있다.

### 두 개 이상의 Configuration 파일 사용 : @Import 활용

- AppConfImport.java

  ```java
  import org.springframework.context.annotation.Import;

  @Configuration
  @Import(AppConf2.class)
  public class AppConfImport {
  ```

- MainForSpring.java
  ```java
  ctx = new AnnotationConfigApplicationContext(AppConfImport.class);
  // 클래스 한 개만 명시해줘도 가능
  ```

### 타입만으로 빈을 구할 수 있다

```java
VersionPrinter versionPrinter = ctx.getBean(MemberPrinter.class);
```

- 다만, 같은 타입의 빈 객체가 2개 이상 존재한다면 에러 발생
