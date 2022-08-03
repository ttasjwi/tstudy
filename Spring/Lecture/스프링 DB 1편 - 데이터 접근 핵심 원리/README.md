
# 스프링 DB 1편 - 데이터 접근 핵심 원리

---

## Chapter 01. JDBC 이해
### <a href="Chapter 01. JDBC 이해/1.1 프로젝트 생성.md" target="_blank">1.1 프로젝트 생성</a>
1) 개발 환경
2) 프로젝트 생성
3) `build.gradle` 설정
4) IDE 설정 (IntelliJ)
5) 동작 확인

### <a href="Chapter 01. JDBC 이해/1.2 H2 데이터베이스 설정.md" target="_blank">1.2 H2 데이터베이스 설정</a>
1) H2 데이터베이스는?
2) H2 데이터베이스 설치
3) H2 데이터베이스 실행
4) DB 파일 생성
5) 기본 테이블 생성하기

### <a href="Chapter 01. JDBC 이해/1.3 JDBC 이해.md" target="_blank">1.3 JDBC 이해</a>
1) 도입 배경 : 표준화되지 않은 데이터베이스 접근 방법
2) JDBC(Java Database Connectivity)
3) JDBC 표준 인터페이스와 JDBC Driver
4) JDBC 도입을 통해 얻어낸 것
5) 순수 JDBC의 한계


### <a href="Chapter 01. JDBC 이해/1.4 JDBC와 최신 데이터 접근 기술.md" target="_blank">1.4 JDBC와 최신 데이터 접근 기술</a>
1) 순수 JDBC(1997)
2) SQL Mapper
3) ORM(Object Relational Mapping)
4) 결국 모든 기술 기반에 JDBC가 있다.

### <a href="Chapter 01. JDBC 이해/1.5 데이터베이스 연결.md" target="_blank">1.5 데이터베이스 연결</a>
1) (실습) 커넥션 획득하기
2) JDBC 커넥션 인터페이스와 구현
3) DriverManager를 통한 커넥션 요청 흐름

### <a href="Chapter 01. JDBC 이해/1.6 JDBC 개발 - 등록.md" target="_blank">1.6 JDBC 개발 - 등록</a>
1) 회원 테이블 생성
2) 회원 클래스 생성
3) DriverManager를 이용한 회원 등록 기능 구현(MemberRepositoryV0)
4) 회원 등록 기능 테스트(MemberRepositoryV0Test)

### <a href="Chapter 01. JDBC 이해/1.7 JDBC 개발 - 조회.md" target="_blank">1.7 JDBC 개발 - 조회</a>
1) DriverManager를 이용한 회원 조회 기능 구현(MemberRepositoryV0)
2) ResultSet의 내부 구조 및 사용 방법
3) 회원 등록, 조회 테스트(MemberRepositoryV0Test)

### <a href="Chapter 01. JDBC 이해/1.8 JDBC 개발 - 수정, 삭제.md" target="_blank">1.8 JDBC 개발 - 수정, 삭제</a>
1) DriverManager를 이용한 수정 기능 구현(MemberRepositoryV0)
2) 수정 기능 테스트
3) DriverManager를 이용한 삭제 기능 구현(MemberRepositoryV0)
4) 삭제 기능 테스트

---

## Chapter 02. 커넥션 풀과 DataSource 이해
### <a href="Chapter 02. 커넥션 풀과 DataSource 이해/2.1 커넥션 풀 이해.md" target="_blank">2.1 커넥션 풀 이해</a>
1) 도입 배경 : 데이터베이스 커넥션을 매번 획득하는 방식
2) 커넥션 풀 : 미리 커넥션을 생성해두고 보관
3) 언제든 DB에 SQL을 즉시 전달 가능
4) 커넥션 대여과 반환
5) 커넥션의 수
6) 커넥션 풀 라이브러리

### <a href="Chapter 02. 커넥션 풀과 DataSource 이해/2.2 DataSource 이해.md" target="_blank">2.2 DataSource 이해</a>
1) 커넥션을 획득하는 다양한 방법
2) 커넥션을 획득하는 방법을 변경 시 문제점
3) DataSource : 커넥션을 획득하는 방법을 추상화
4) 커넥션 풀 라이브러리들은 이미 DataSource를 구현함
5) DriverManagerDataSource : Spring의 지원

### <a href="Chapter 02. 커넥션 풀과 DataSource 이해/2.3 DataSource 예제1 - DriverManager.md" target="_blank">2.3 DataSource 예제1 - DriverManager</a>
1) (실습) DriverManager를 통해 커넥션 획득
2) (실습) DriverManagerDataSource를 통해 커넥션 획득
3) DriverManager vs DriverManagerDataSource
4) 설정과 사용의 분리

### <a href="Chapter 02. 커넥션 풀과 DataSource 이해/2.4 DataSource 예제2 - 커넥션 풀.md" target="_blank">2.4 DataSource 예제2 - 커넥션 풀</a>
1) (실습) HikariDataSource를 통해 커넥션 획득
2) (실습) HikariDataSource를 통해 커넥션 획득 - 실행 로그 분석

### <a href="Chapter 02. 커넥션 풀과 DataSource 이해/2.5 DataSource 적용.md" target="_blank">2.5 DataSource 적용</a>
1) DataSource 의존관계 주입 - MemberRepositoryV1
2) 자원 반환 - JdbcUtils
3) 리포지토리 테스트 - MemberRepositoryV1Test
4) DataSource 의존의 이점 : DI, OCP

---

## Chapter 03. 트랜잭션 이해
### <a href="Chapter 03. 트랜잭션 이해/3.01 트랜잭션 - 개념 이해.md" target="_blank">3.01 트랜잭션 - 개념 이해</a>
1) 트랜잭션(Transaction)
2) 커밋과 롤백
3) 트랜잭션의 4대 특성 : ACID
4) 트랜잭션의 격리 수준 완화에 따라 일어나는 현상들
5) 트랜잭션 격리 수준 - Isolation level

### <a href="Chapter 03. 트랜잭션 이해/3.02 데이터베이스 연결 구조와 DB 세션.md" target="_blank">3.02 데이터베이스 연결 구조와 DB 세션</a>
1) 커넥션과 데이터베이스 세션
2) SQL, 트랜잭션 실행의 주체는 DB 세션
3) 커넥션 풀과 DB 세션

### <a href="Chapter 03. 트랜잭션 이해/3.03 트랜잭션 - DB 예제1 - 개념 이해.md" target="_blank">3.03 트랜잭션 - DB 예제1 - 개념 이해</a>
1) 트랜잭션 사용법
2) (예제) 세션1에서 신규 데이터 추가
3) 커밋하지 않은 데이터를 다른 곳에서 조회할 수 있을 때(READ UNCOMMITTED)
4) (예제) 세션1 신규 데이터 추가 후 commit
5) (예제) 세션1 신규 데이터 추가 후 rollback

### <a href="Chapter 03. 트랜잭션 이해/3.04 트랜잭션 - DB 예제2 - 자동 커밋, 수동 커밋.md" target="_blank">3.04 트랜잭션 - DB 예제2 - 자동 커밋, 수동 커밋</a>
1) 자동 커밋
2) 수동 커밋


### <a href="Chapter 03. 트랜잭션 이해/3.05 트랜잭션 - DB 예제3 - 트랜잭션 실습.md" target="_blank">3.05 트랜잭션 - DB 예제3 - 트랜잭션 실습</a>
1) (실습) 실습 환경 준비
2) (실습) 신규 데이터 추가 - 커밋 전
3) (실습) 세션1에서 커밋했을 때
4) (실습) 세션1에서 롤백했을 때

### <a href="Chapter 03. 트랜잭션 이해/3.06 트랜잭션 - DB 예제4 - 계좌이체.md" target="_blank">3.06 트랜잭션 - DB 예제4 - 계좌이체</a>
1) (실습) 계좌이체 정상
2) (실습) 계좌이체 문제 상황에서, 강제 커밋할 때
3) (실습) 계좌이체 문제 상황에서, 롤백
4) 트랜잭션의 원자성
5) 비즈니스 로직은 반드시 트랜잭션에서 이루어져야한다.

### <a href="Chapter 03. 트랜잭션 이해/3.07 DB 락 - 개념 이해.md" target="_blank">3.07 DB 락 - 개념 이해</a>
1) 동시 수정의 위험성
2) 데이터 변경(update, delete) 시도 → 락 획득
3) Timeout 안에 락을 획득하지 못 하면 예외가 발생
4) (예제) 동시 변경 시도와 락

### <a href="Chapter 03. 트랜잭션 이해/3.08 DB 락 - 변경.md" target="_blank">3.08 DB 락 - 변경</a>
1) (실습) 동시 변경 시도와 락
2) (실습) 세션2 락 타임아웃

### <a href="Chapter 03. 트랜잭션 이해/3.09 DB 락 - 조회.md" target="_blank">3.09 DB 락 - 조회</a>
1) 일반적인 조회는 락을 사용하지 않는다.
2) 조회 시 락을 획득하는 방법 : SELECT ~ FOR UPDATE
3) 조회 시점에 락이 필요한 경우 : 강제로 외부의 수정을 막아야 할 때
4) (실습) 조회 시 락 획득
5) 각 DB마다 트랜잭션, 락 동작이 다르다.

### <a href="Chapter 03. 트랜잭션 이해/3.10 트랜잭션 - 적용1.md" target="_blank">3.10 트랜잭션 - 적용1</a>
1) (실습) 트랜잭션 없이 비즈니스 로직 구현 - MemberServiceV1
2) (실습) 테스트 환경 준비 - MemberServiceV1Test
3) (실습) 정상 이체 상황 테스트
4) (실습) 이체중 예외 발생 상황 테스트

### <a href="Chapter 03. 트랜잭션 이해/3.11 트랜잭션 - 적용2.md" target="_blank">3.11 트랜잭션 - 적용2</a>
1) 트랜잭션은 서비스 계층에서 시작되고 끝나야 한다.
2) 트랜잭션을 사용하는 동안 같은 커넥션을 유지해야한다.
3) (실습) 리포지토리에 커넥션 전달 - MemberRepositoryV2
4) (실습) 서비스 계층에 트랜잭션 도입 - MemberServiceV2
5) (실습) 테스트 환경 준비 - MemberServiceV2Test
6) (실습) 정상 이체 상황 테스트
7) (실습) 이체중 예외 발생 상황 테스트
8) 한계점 - 트랜잭션 적용 후 서비스 계층의 코드가 복잡해짐

---

## Chapter 04. 스프링과 문제 해결 - 트랜잭션
### <a href="Chapter 04. 스프링과 문제 해결 - 트랜잭션/4.01 문제점들.md" target="_blank">4.01 문제점들</a>
1) 애플리케이션 구조
2) 서비스 계층을 특정 기술에 종속적이지 않게 개발해야 한다.
3) MemberServiceV1의 문제점
4) MemberServiceV2의 문제점
5) 트랜잭션 문제
6) 데이터 접근 계층의 JDBC 구현 기술 예외가 서비스 계층으로 누수
7) 순수 JDBC의 문제 - 반복문제
8) 스프링을 통해 문제 해결

### <a href="Chapter 04. 스프링과 문제 해결 - 트랜잭션/4.02 트랜잭션 추상화.md" target="_blank">4.02 트랜잭션 추상화</a>
1) 데이터 접근 기술 변경 시 트랜잭션 코드도 변경해야한다.
2) 트랜잭션을 추상화
3) 스프링의 트랜잭션 추상화 - PlatformTransactionManager

### <a href="Chapter 04. 스프링과 문제 해결 - 트랜잭션/4.03 트랜잭션 동기화.md" target="_blank">4.03 트랜잭션 동기화</a>
1) 트랜잭션 유지를 위해 커넥션을 유지해야하는 불편함
2) 트랜잭션 동기화 매니저

### <a href="Chapter 04. 스프링과 문제 해결 - 트랜잭션/4.04 트랜잭션 문제 해결 - 트랜잭션 매니저1.md" target="_blank">4.04 트랜잭션 문제 해결 - 트랜잭션 매니저1</a>
1) (실습) 트랜잭션 매니저 적용 : MemberRepositoryV3
2) (실습) 트랜잭션 매니저 적용 : MemberServiceV3_1
3) (실습) 트랜잭션 매니저 적용 테스트 : MemberServiceV3_1

### <a href="Chapter 04. 스프링과 문제 해결 - 트랜잭션/4.05 트랜잭션 문제 해결 - 트랜잭션 매니저2.md" target="_blank">4.05 트랜잭션 문제 해결 - 트랜잭션 매니저2</a>
1) 트랜잭션 매니저 기반 트랜잭션 흐름1 : 트랜잭션 시작
2) 트랜잭션 매니저 기반 트랜잭션 흐름2 : 로직 실행
3) 트랜잭션 매니저 기반 트랜잭션 흐름3 : 트랜잭션 종료
4) 결론 : 트랜잭션의 추상화, 동기화 성공
5) 아직 남아있는 문제 : 예외 누수

### <a href="Chapter 04. 스프링과 문제 해결 - 트랜잭션/4.06 트랜잭션 문제 해결 - 트랜잭션 템플릿.md" target="_blank">4.06 트랜잭션 문제 해결 - 트랜잭션 템플릿</a>
1) 트랜잭션 사용 → 서비스 로직마다 중복코드
2) 트랜잭션 템플릿 : 트랜잭션을 템플릿 콜백 패턴으로 공통화
3) (실습) 트랜잭션 템플릿 적용 : MemberServiceV3_2
4) (실습) 트랜잭션 템플릿 적용 테스트 : MemberServiceV3_2
5) 한계 : 서비스 로직에 아직도 트랜잭션 기술이 남아있음

### 4.07 트랜잭션 문제 해결 - 트랜잭션 AOP 이해
### 4.08 트랜잭션 문제 해결 - 트랜잭션 AOP 적용
### 4.09 트랜잭션 문제 해결 - 트랜잭션 AOP 정리
### 4.10 스프링 부트의 자동 리소스 등록

---

## Chapter 05. 자바 예외 이해
### 5.1 예외 계층
### 5.2 예외 기본 규칙
### 5.3 체크 예외 기본 이해
### 5.4 언체크 예외 기본 이해
### 5.5 체크 예외 활용
### 5.6 언체크 예외 활용
### 5.7 예외 포함과 스택 트레이스

---

## Chapter 06. 스프링과 문제 해결 - 예외 처리, 반복
### 6.1 체크 예외와 인터페이스
### 6.2 런타임 예외 적용
### 6.3 데이터 접근 예외 직접 만들기
### 6.4 스프링 예외 추상화 이해
### 6.5 스프링 예외 추상화 적용
### 6.6 JDBC 반복 문제 해결 - JdbcTemplate

---
