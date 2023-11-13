## library dependencies 구조

- main
  - spring-boot-starter-web
    - tomcat : embed tomcat 가지고 있음
    - spring-webmvc
  - spring-boot-starter-thymeleaf
  - spring-boot-starter-data-jpa
    - aop
      - spring-boot-starter
        - logging
          - logback
          - slf4j
        - spring-boot
          - spring-core
    - jdbc
      - HikariCP : 커넥션 풀
      - spring-jdbc
        - transaction
        - jdbcTemplate
    - hibernate
    - spring-data-jpa

- test
  - spring-boot-starter-test
    - junit
    - spring-test
    - mockito
    - assertj
  - h2database

## 핵심 라이브러리
- 스프링 MVC
- 스프링 ORM
- JPA, 하이버네이트
- 스프링 데이터 JPA

## 기타 라이브러리
- H2 데이터베이스 클라이언트
- 커넥션 풀 : 부트 기본은 HikariCP
- WEB(thymeleaf)
- 로깅 SLF4J & LogBack
- 테스트