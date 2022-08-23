
# 스프링 DB 2편 - 데이터 접근 활용 기술

---

## Chapter 01. 데이터 접근 기술 - 시작

### <a href="Chapter 01. 데이터 접근 기술 - 시작/1.1 데이터 접근 기술 진행 방식 소개.md" target="_blank">1.1 데이터 접근 기술 진행 방식 소개</a>
1) SQL Mapper
2) ORM(Object Relational Mapping)
3) 본 강의의 진행방식 및 목표

### <a href="Chapter 01. 데이터 접근 기술 - 시작/1.2 프로젝트 설정과 메모리 저장소.md" target="_blank">1.2 프로젝트 설정과 메모리 저장소</a>
1) 프로젝트 설정 순서
2) 실행 확인

### <a href="Chapter 01. 데이터 접근 기술 - 시작/1.3 프로젝트 구조 설명1 - 기본.md" target="_blank">1.3 프로젝트 구조 설명1 - 기본</a>
1) 프로젝트 설정
2) 도메인 분석(Item)
3) 리포지토리 및 필요 DTO 분석
4) 서비스 분석(ItemService, ItemServiceV1)
5) DTO는 무엇이고 어디에 두어야할까?

### <a href="Chapter 01. 데이터 접근 기술 - 시작/1.4 프로젝트 구조 설명2 - 설정.md" target="_blank">1.4 프로젝트 구조 설명2 - 설정</a>
1) 메모리 리포지토리, 서비스 수동 빈 등록 - MemoryConfig
2) 확인용 초기 데이터 삽입 - TestDataInit
3) 메인 실행 클래스 - ItemServiceApplication
4) 스프링 프로필(Profile)
5) 스프링 테스트 프로필

### <a href="Chapter 01. 데이터 접근 기술 - 시작/1.5 프로젝트 구조 설명3 - 테스트.md" target="_blank">1.5 프로젝트 구조 설명3 - 테스트</a>
1) 인터페이스를 의존하는 테스트
2) 테스트 종료 후 데이터 소멸 (for MemoryItemRepository)
3) 리포지토리 테스트 코드

### <a href="Chapter 01. 데이터 접근 기술 - 시작/1.6 데이터베이스 테이블 생성.md" target="_blank">1.6 데이터베이스 테이블 생성</a>
1) Item DDL 및 테이블 생성
2) 테이블 동작 확인
3) 기본키(Primary Key) - 자연키와 대리키
4) 자연키 대신 대리키를 기본키로 사용하자.

---

## Chapter 02. 데이터 접근 기술 - 스프링 JdbcTemplate
### <a href="Chapter 02. 데이터 접근 기술 - 스프링 JdbcTemplate/2.1 JdbcTemplate 소개와 설정.md" target="_blank">2.1 JdbcTemplate 소개와 설정</a>
1) 설정이 편리하다.
2) 순수 Jdbc의 반복 문제를 해결했다.
3) 단점 : SQL 작성의 수고, 난해한 동적 SQL
4) 의존 라이브러리 추가(spring-jdbc, H2 데이터베이스 드라이버)

### <a href="Chapter 02. 데이터 접근 기술 - 스프링 JdbcTemplate/2.2 JdbcTemplate 적용1 - 기본.md" target="_blank">2.2 JdbcTemplate 적용1 - 기본</a>
1) JdbcTemplateRepositoryV1 - JdbcTemplate 사용
2) 데이터 저장 기능 - save()
3) 데이터 갱신 기능 - update()
4) 데이터 단건 조회 기능 - findById()
5) 데이터 검색 기능 - findAll() : 동적 쿼리
6) RowMapper : 조회 결과를 객체로 바인딩

### <a href="Chapter 02. 데이터 접근 기술 - 스프링 JdbcTemplate/2.3 JdbcTemplate 적용2 - 동적 쿼리 문제.md" target="_blank">2.3 JdbcTemplate 적용2 - 동적 쿼리 문제</a>
1) JdbcTemplate 기술의 한계 - 동적 쿼리 문제

### <a href="Chapter 02. 데이터 접근 기술 - 스프링 JdbcTemplate/2.4 JdbcTemplate 적용3 - 구성과 실행.md" target="_blank">2.4 JdbcTemplate 적용3 - 구성과 실행</a>
1) 리포지토리 설정 변경 - JdbcTemplateV1Config
2) 데이터베이스 접근 설정 : datasource 설정
3) 실행 확인
4) JdbcTemplate SQL 로그 확인 - 로깅 설정

### <a href="Chapter 02. 데이터 접근 기술 - 스프링 JdbcTemplate/2.5 JdbcTemplate - 이름 지정 파라미터 1.md" target="_blank">2.5 JdbcTemplate - 이름 지정 파라미터 1</a>
1) 순서기반 파라미터 바인딩의 문제점
2) JdbcTemplateRepositoryV2 - NamedParameterJdbcTemplate 사용(이름 기반 바인딩)
3) sql에 파라미터 기입
4) Insert 후 데이터베이스 생성 키를 쉽게 조회 가능

### <a href="Chapter 02. 데이터 접근 기술 - 스프링 JdbcTemplate/2.6 JdbcTemplate - 이름 지정 파라미터 2.md" target="_blank">2.6 JdbcTemplate - 이름 지정 파라미터 2</a>
1) 이름 지정 파라미터 전달 방법들
2) Map을 통한 파라미터 전달
3) MapSqlParameterSource를 통한 파라미터 전달
4) BeanPropertySqlParameterSource을 통한 파라미터 전달
5) 조회 결과 바인딩 - BeanPropertyRowMapper

### <a href="Chapter 02. 데이터 접근 기술 - 스프링 JdbcTemplate/2.7 JdbcTemplate - 이름 지정 파라미터 3.md" target="_blank">2.7 JdbcTemplate - 이름 지정 파라미터 3</a>
1) 리포지토리 설정 변경 - JdbcTemplateV2Config
2) 실행 확인

### <a href="Chapter 02. 데이터 접근 기술 - 스프링 JdbcTemplate/2.8 JdbcTemplate - SimpleJdbcInsert.md" target="_blank">2.8 JdbcTemplate - SimpleJdbcInsert</a>
1) JdbcTemplateRepositoryV3 - SimpleJdbcInsert 추가
2) `save()` 수정 - SimpleJdbcInsert 적용
3) SimpleJdbcInsert 로깅 확인
4) 리포지토리 설정 변경 - JdbcTemplateV3Config
5) 실행 확인

### <a href="Chapter 02. 데이터 접근 기술 - 스프링 JdbcTemplate/2.9 JdbcTemplate 기능 정리.md" target="_blank">2.9 JdbcTemplate 기능 정리</a>
1) JdbcTemplate의 주요 클래스
2) JdbcTemplate - 조회
3) JdbcTemplate - 변경(INSERT, UPDATE, DELETE)
4) JdbcTemplate - 기타 기능(DDL, 스토어드 프로시저 호출 등)
5) 실무 : SQL 직접 작성이 필요하면 JdbcTemplate
6) JdbcTemplate의 한계 - 동적쿼리

---

## Chapter 03. 데이터 접근 기술 - 테스트
### <a href="Chapter 03. 데이터 접근 기술 - 테스트/3.1 테스트 - 데이터베이스 연동.md" target="_blank">3.1 테스트 - 데이터베이스 연동</a>
1) 테스트 실행 시, 데이터베이스 연동
2) `@SpringBootTest` : `@SpringBootApplication`을 찾아 설정으로 사용
3) 실사용 DB를 연동하여 테스트 실행 - 실패
4) 실사용 DB와 테스트용 DB는 격리되어야 한다.

### <a href="Chapter 03. 데이터 접근 기술 - 테스트/3.2 테스트 - 데이터베이스 분리.md" target="_blank">3.2 테스트 - 데이터베이스 분리</a>
1) 실사용 DB, 테스트 DB 분리
2) 테스트 DB를 연동하여 테스트 실행 - 반복 실행 시 실패
3) 한계 : 테스트 결과가 다른 테스트에 영향을 끼침, 반복 실행 불가능

### <a href="Chapter 03. 데이터 접근 기술 - 테스트/3.3 테스트 - 데이터 롤백.md" target="_blank">3.3 테스트 - 데이터 롤백</a>
1) 트랜잭션과 롤백 전략
2) 테스트에 트랜잭션 추가
3) 테스트 반복 실행

### <a href="Chapter 03. 데이터 접근 기술 - 테스트/3.4 테스트 - @Transactional.md" target="_blank">3.4 테스트 - @Transactional</a>
1) 테스트 코드에 `@Transactional` 적용
2) `@Transactional`의 동작 원리
3) 테스트 트랜잭션의 전파
4) 테스트 코드에 트랜잭션을 도입함으로서 얻은 이득
5) 강제로 테스트코드 커밋하기 - `@Commit`

### <a href="Chapter 03. 데이터 접근 기술 - 테스트/3.5 테스트 - 임베디드 모드 DB.md" target="_blank">3.5 테스트 - 임베디드 모드 DB</a>
1) H2 데이터베이스의 임베디드 모드 DB 기능
2) H2 데이터베이스 임베디드 모드 수동 설정
3) (실습) 임베디드 DB 상태로 테스트 실행 - 실패
4) 스프링 부트 : 기본 SQL 스크립트를 통해 데이터베이스를 초기화
5) (실습) SQL 스크립트 등록 후 테스트 실행 - 성공

### <a href="Chapter 03. 데이터 접근 기술 - 테스트/3.6 테스트 - 스프링 부트와 임베디드 모드.md" target="_blank">3.6 테스트 - 스프링 부트와 임베디드 모드</a>
1) 테스트 datasource 설정 제거 -> 임베디드 데이터베이스
2) Datasource 설정 없이 테스트 코드 실행 → 성공
3) 임베디드 데이터베이스 관련 설정

---

## Chapter 04. 데이터 접근 기술 - MyBatis
### <a href="Chapter 04. 데이터 접근 기술 - MyBatis/4.1 MyBatis 소개.md" target="_blank">4.1 MyBatis 소개</a>
1) MyBatis란?
2) SQL을 XML로 작성
3) 동적 쿼리를 편리하게 작성
4) 단점 : 약간의 설정이 필요하다.
5) JdbcTemplate vs MyBatis
6) MyBatis 공식 사이트(메뉴얼)

### <a href="Chapter 04. 데이터 접근 기술 - MyBatis/4.2 MyBatis 설정.md" target="_blank">4.2 MyBatis 설정</a>
1) `build.gradle`에 MyBatis 의존관계 추가
2) `application.properties`에 MyBatis 설정 추가

### <a href="Chapter 04. 데이터 접근 기술 - MyBatis/4.3 MyBatis 적용1 - 기본.md" target="_blank">4.3 MyBatis 적용1 - 기본</a>
1) Mapper 인터페이스 생성
2) XML 경로 설정
3) XML 작성
4) 기본 SQL 매핑법
5) 동적쿼리 작성
6) XML 특수 문자 처리

### <a href="Chapter 04. 데이터 접근 기술 - MyBatis/4.4 MyBatis 적용2 - 설정과 실행.md" target="_blank">4.4 MyBatis 적용2 - 설정과 실행</a>
1) MyBatisItemRepository - MyBatis 적용
2) 리포지토리 설정 변경 - MyBatisConfig
3) 테스트 및 애플리케이션 실행

### <a href="Chapter 04. 데이터 접근 기술 - MyBatis/4.5 MyBatis 적용3 - 분석.md" target="_blank">4.5 MyBatis 적용3 - 분석</a>
1) Mapper 구현체 생성 및 스프링 빈 등록 원리
2) MyBatis 스프링 연동 모듈과 Mapper 구현체

### <a href="Chapter 04. 데이터 접근 기술 - MyBatis/4.6 MyBatis 기능 정리1 - 동적 쿼리.md" target="_blank">4.6 MyBatis 기능 정리1 - 동적 쿼리</a>
1) MyBatis 관련 메뉴얼
2) MyBatis 동적 SQL 상세 기능
3) if / choose, when, otherwise
4) where, set, trim
5) foreach

### <a href="Chapter 04. 데이터 접근 기술 - MyBatis/4.7 MyBatis 기능 정리2 - 기타 기능.md" target="_blank">4.7 MyBatis 기능 정리2 - 기타 기능</a>
1) 어노테이션으로 SQL 작성
2) 문자열 대체(String Substitution)
3) 재사용 가능한 SQL 조각
4) 조회 결과를 매핑하는 여러가지 방법들

---

## Chapter 05. 데이터 접근 기술 - JPA
### <a href="Chapter 05. 데이터 접근 기술 - JPA/5.1 JPA 시작.md" target="_blank">5.1 JPA 시작</a>
1) ORM(Object Relational Mapping)
2) JPA는 자바의 핵심 ORM 데이터 기술이다
3) 실무 : JPA + Spring Data JPA + Querydsl

### 5.2 ORM 개념1 - SQL 중심적인 개발의 문제점

### 5.3 ORM 개념2 - JPA 소개

### <a href="Chapter 05. 데이터 접근 기술 - JPA/5.4 JPA 설정.md" target="_blank">5.4 JPA 설정</a>
1) `build.gradle`에 Spring Data JPA 의존관계 추가
2) `application.properties`에 로깅설정 추가

### <a href="Chapter 05. 데이터 접근 기술 - JPA/5.5 JPA 적용1 - 개발.md" target="_blank">5.5 JPA 적용1 - 개발</a>
1) 객체 - ORM 매핑
2) 주의점 : 기본생성자 필수
3) 순수 JPA 리포지토리 생성 - JpaItemRepositoryV1
4) 스프링부트의 JPA 자동 설정
5) 리포지토리 설정 변경 - JpaConfig
6) 테스트 및 애플리케이션 실행

### <a href="Chapter 05. 데이터 접근 기술 - JPA/5.6 JPA 적용2 - 리포지토리 분석.md" target="_blank">5.6 JPA 적용2 - 리포지토리 분석</a>
1) `save()` - 저장
2) `update()` - 수정
3) `findById()` - 단건 조회
4) `findAll()` - 목록 조회
5) 한계 : 복잡한 동적쿼리

### <a href="Chapter 05. 데이터 접근 기술 - JPA/5.7 JPA 적용3 - 예외 변환.md" target="_blank">5.7 JPA 적용3 - 예외 변환</a>
1) 순수 JPA 기술은 스프링과 관계 없는 JPA 예외를 발생시킨다.
2) 스프링의 JPA 예외 추상화 : `@Repository`

---

## Chapter 06. 데이터 접근 기술 - 스프링 데이터 JPA
### 6.1 스프링 데이터 JPA 소개1 - 등장 이유
### 6.2 스프링 데이터 JPA 소개2 - 기능

### <a href="Chapter 06. 데이터 접근 기술 - 스프링 데이터 JPA/6.3 스프링 데이터 JPA 주요 기능.md" target="_blank">6.3 스프링 데이터 JPA 주요 기능</a>
1) 공통 인터페이스 기능 : `JpaRepository` 인터페이스 상속
2) 쿼리 메서드 기능
3) 어노테이션을 통해 JPQL 직접 사용하기 : `@Query`

### <a href="Chapter 06. 데이터 접근 기술 - 스프링 데이터 JPA/6.4 스프링 데이터 JPA 적용1.md" target="_blank">6.4 스프링 데이터 JPA 적용1</a>
1) 설정 - `build.gradle`
2) Spring Data Jpa 인터페이스 - SpringDataJpaItemRepository
3) 쿼리 메서드 기능 적용
4) 어노테이션을 통해 JPQL을 직접 작성하는 기능 적용

### <a href="Chapter 06. 데이터 접근 기술 - 스프링 데이터 JPA/6.5 스프링 데이터 JPA 적용2.md" target="_blank">6.5 스프링 데이터 JPA 적용2</a>
1) JpaItemRepositoryV2 - Spring Data JPA 적용
2) 리포지토리 분석
3) 스프링 데이터 JPA의 예외 변환
4) 리포지토리 설정 변경 - SpringDataJpaConfig
5) 테스트 및 애플리케이션 실행
6) (추가) 하이버네이트 버그(스프링 부트 2.6.5, 하이버네이트 5.6.7)

---

## Chapter 07. 데이터 접근 기술 - Querydsl

### 7.1 Querydsl 소개1 - 기존 방식의 문제점
### 7.2 Querydsl 소개2 - 해결

### <a href="Chapter 07. 데이터 접근 기술 - Querydsl/7.3 Querydsl 설정.md" target="_blank">7.3 Querydsl 설정</a>
1) `build.gradle` 의존성 추가
2) Build Tools 설정
3) Gradle 방식 - Q타입 생성 확인 방법
4) IntelliJ IDEA 방식 - Q타입 생성 확인
5) 각 버전마다 설정이 조금씩 다르다.

### <a href="Chapter 07. 데이터 접근 기술 - Querydsl/7.4 Querydsl 적용.md" target="_blank">7.4 Querydsl 적용</a>
1) JpaItemRepositoryV3 - Querydsl 적용
2) `save()`, `update()`, `findById()`
3) `findAllOld()` - BooleanBuilder를 활용한 동적쿼리
4) `findAll()` - BooleanExpression을 활용한 동적쿼리 작성
5) Querydsl은 예외 변환을 지원하지 않는다.
6) 리포지토리 설정 변경 - QuerydslConfig
7) 테스트 및 애플리케이션 실행
8) Querydsl의 장단점

---

## Chapter 08. 데이터 접근 기술 - 활용 방안
### <a href="Chapter 08. 데이터 접근 기술 - 활용 방안/8.1 스프링 데이터 JPA 예제와 트레이드 오프.md" target="_blank">8.1 스프링 데이터 JPA 예제와 트레이드 오프</a>
1) 어댑터 사용의 장점 : 구조적 안정성
2) 어댑터 사용의 단점 : 복잡도 증가, 유지보수 비용 증가
3) 객체 의존관계를 변경할 때 : 단순한 구조와 개발 편의성
4) 트레이드 오프

### <a href="Chapter 08. 데이터 접근 기술 - 활용 방안/8.2 실용적인 구조.md" target="_blank">8.2 실용적인 구조</a>
1) 스프링 데이터 JPA + Querydsl
2) ItemRepositoryV2 : 스프링 데이터 JPA
3) ItemQueryRepositoryV2 : Querydsl
4) ItemServiceV2
5) 서비스, 리포지토리 설정 변경 - V2Config
6) 테스트 및 애플리케이션 실행
7) 다른 방안 : 커스텀 리포지토리

### <a href="Chapter 08. 데이터 접근 기술 - 활용 방안/8.3 다양한 데이터 접근 기술 조합.md" target="_blank">8.3 다양한 데이터 접근 기술 조합</a>
1) 데이터 접근 기술 선택
2) 기본은 ORM + 최후의 보루 SQLMapper
3) 트랜잭션 매니저 선택
4) 주의 : JPA 플러시 타이밍에 주의

---

## Chapter 09. 스프링 트랜잭션 이해
### <a href="Chapter 09. 스프링 트랜잭션 이해/9.01 스프링 트랜잭션 소개.md" target="_blank">9.01 스프링 트랜잭션 소개</a>
1) 스프링 트랜잭션 추상화
2) 스프링 트랜잭션 사용 방식
3) 선언적 트랜잭션과 AOP
4) 프록시 도입 후 전체 과정
5) 스프링이 제공하는 트랜잭션 AOP : `@Transactional`

### <a href="Chapter 09. 스프링 트랜잭션 이해/9.02 프로젝트 생성.md" target="_blank">9.02 프로젝트 생성</a>
작성 중

### <a href="Chapter 09. 스프링 트랜잭션 이해/9.03 트랜잭션 적용 확인.md" target="_blank">9.03 트랜잭션 적용 확인</a>
작성 중

### <a href="Chapter 09. 스프링 트랜잭션 이해/9.04 트랜잭션 적용 위치.md" target="_blank">9.04 트랜잭션 적용 위치</a>
작성 중

### <a href="Chapter 09. 스프링 트랜잭션 이해/9.05 트랜잭션 AOP 주의 사항 - 프록시 내부 호출1.md" target="_blank">9.05 트랜잭션 AOP 주의 사항 - 프록시 내부 호출1</a>
작성 중

### <a href="Chapter 09. 스프링 트랜잭션 이해/9.06 트랜잭션 AOP 주의 사항 - 프록시 내부 호출2.md" target="_blank">9.06 트랜잭션 AOP 주의 사항 - 프록시 내부 호출2</a>
작성 중

### <a href="Chapter 09. 스프링 트랜잭션 이해/9.07 트랜잭션 AOP 주의 사항 - 초기화 시점.md" target="_blank">9.07 트랜잭션 AOP 주의 사항 - 초기화 시점</a>
작성 중

### <a href="Chapter 09. 스프링 트랜잭션 이해/9.08 트랜잭션 옵션 소개.md" target="_blank">9.08 트랜잭션 옵션 소개</a>
작성 

### <a href="Chapter 09. 스프링 트랜잭션 이해/9.09 예외와 트랜잭션 커밋, 롤백 - 기본.md" target="_blank">9.09 예외와 트랜잭션 커밋, 롤백 - 기본</a>
작성 중

### <a href="Chapter 09. 스프링 트랜잭션 이해/9.10 예외와 트랜잭션 커밋, 롤백 - 활용.md" target="_blank">9.10 예외와 트랜잭션 커밋, 롤백 - 활용</a>
작성 중

---

## Chapter 10. 스프링 트랜잭션 전파1 - 기본
### 10.1 스프링 트랜잭션 전파1 - 커밋, 롤백
### 10.2 스프링 트랜잭션 전파2 - 트랜잭션 두 번 사용
### 10.3 스프링 트랜잭션 전파3 - 전파 기본
### 10.4 스프링 트랜잭션 전파4 - 전파 예제
### 10.5 스프링 트랜잭션 전파5 - 외부 롤백
### 10.6 스프링 트랜잭션 전파6 - 내부 롤백 
### 10.7 스프링 트랜잭션 전파7 - REQUIRES_NEW
### 10.8 스프링 트랜잭션 전파8 - 다양한 전파 옵션

---

## Chapter 11. 스프링 트랜잭션 전파2 - 활용
### 11.1 트랜잭션 전파 활용1 - 예제 프로젝트 시작
### 11.2 트랜잭션 전파 활용2 - 커밋, 롤백
### 11.3 트랜잭션 전파 활용3 - 단일 트랜잭션
### 11.4 트랜잭션 전파 활용4 - 전파 커밋
### 11.5 트랜잭션 전파 활용5 - 전파 롤백
### 11.6 트랜잭션 전파 활용6 - 복구 REQUIRED
### 11.7 트랜잭션 전파 활용7 - 복구 REQUIRES_NEW

---
