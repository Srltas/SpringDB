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
 
## 22.06.01
* 스프링 데이터 JPA
  - JpaRepository 인터페이스를 통해 기본적인 CRUD 기능 제공
  - 쿼리 메서드 기능을 통해 메소드 이름을 분석해 쿼리르 자동 생성
  - 스프링 데이터 JPA가 만들어주는 프록시에서 이미 예외 변환을 처리해주기 때문에 @Repository와 관계 없이 스프링 예외 추상화 지원 가능

* Querydsl
  - Querydsl은 JPAOueryFactory가 필요하고, JPAQueryFactory는 EntityManager가 필요
  - 동적 쿼리를 깔끔하게 만들 수 있으며, 쿼리 문장에 오류가 있어도 컴파일 시점에 오류를 막을 수 있음
  - 반복되는 코드를 메소드로 만들어서 다른 쿼리에 재사용할 수 있음
 
* 다양한 데이터 접근 기술 조합
  - JPA와 JdbcTemplate or MyBatis를 함께 쓸 때 JpaTransactionManager를 사용
  - JPA도 DataSource와 JDBC 커넥션을 사용해 DB와 연결되는 것으로 JpaTransactionManager로 모두 하나의 트랜잭션으로 묶어 사용 가능

* 스프링 트랜잭션 이해
  - @Transactional이 붙은 클래스, 메소드는 트랜잭션 AOP를 통해 프록시를 만들어 컨테이너에 등록
  - 프록시를 통해 트랜잭션을 관리하기 때문에 대상 객체의 내부에서 메서드 호출이 발생하면 프록시를 거치지 않고 대상 객체를 직접 호출하기 때문에 트랜잭션이 적용 안됨
  - 코드 예제에서는 대상 객체의 내부에서 호출된 메서드를 별도 클래스로 분리하여 해결
  - 스프링 트랜잭션 AOP는 public 메서드에만 트랜잭션이 적용됨
  - @PostConstruct을 이용해 초기화 시 초기화 코드가 먼저 실행되고 트랜잭션 AOP가 적용되기 때문에 초기화 시점에 메서드들이 트랜잭션을 획득할 수 없음
  - @EventListener(value = ApplicationReadyEvent.class)를 통해 스프링 컨테이너가 완전히 생성된 후 메서드를 호출해 트랜잭션을 얻을 수 있음
  - 스프링은 체크 예외는 커밋하고, 런타임 예외는 롤백함
