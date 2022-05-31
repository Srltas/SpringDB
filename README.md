# SpringDB 1
김영한님의 스프링 DB 1편 강의 학습 내용 정리 및 기록

## 22.05.07
* (강의) JDBC 표준 인터페이스, JDBC DriverManager 연결 이해 학습
* (강의) 커넥션 풀, DataSource 학습

## 22.05.08
* (강의) 트랜잭션 DB 연결 구조, DB락 학습, 트랜잭션 예제코드 코딩
* (강의) 트랜잭션 매니저, 트랜잭션 템플릿, 트랜잭션 AOP 학습
* (강의) 자바 예외 기본 개념 학습
* (강의) 런타임 예외, 스프링 예외 추상화, JdbcTemplate 적용

# SpringDB 2
김영한님의 스프링 DB 2편 강의 학습 내용 정리 및 기록

## 22.05.30
* JdbcTemplate : 순서 기반 파라미터 바인딩 지원
  - KeyHolder를 사용해 DB PK ID값을 확인
  
* NamedParameterJdbcTemplate : 이름 기반 파라미터 바인딩을 지원
  - '?' 대신 ':파라미터이름 을 사용'
  - Map, MapSqlParameterSource, BeanPropertySqlParameterSource 등 다양한 방법으로 파라미터 객체 생성 가능
 
* SimpleJdbcInsert : INSERT SQL을 편리하게 사용 가능

## 22.05.31
* 데이터베이스를 연동하여 테스트 케이스 작성
  - @Transactional을 활용해 테스트 케이스가 다른 테스트 케이스와 격리되고, 반복해서 실행할 수 있게 만듦
  - 임베디드 모드 DB로 JVM 안에서 메모리 모드로 동작하게 만들어 DB 연결이 안되어 있어도 테스트를 할 수 있게 설정
  
* MyBatis 적용
  - 매핑 XML, 매퍼 인터페이스를 만들어 JAVA코드와 SQL 매핑
  - MyBatis의 장점인 동적 쿼리를 만들어 사용
  - MyBatis 스프링 연동 모듈에서 매퍼 인터페이스에 대한 구현체를 동적 프록시로 생성함

* JPA 적용
  - @Entity, @Id, @GeneratedValue, @Column 등 어노테이션을 이용해 엔티티를 만들어 JPA 적용
  - JPQL(객체지향 쿼리 언어) 학습
  - @Repository이 붙어 있는 클래스는 예외 변환 AOP의 적용 대상이 되어 JPA 예외를 Spring 예외로 추상화 시켜줌
