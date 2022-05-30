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
