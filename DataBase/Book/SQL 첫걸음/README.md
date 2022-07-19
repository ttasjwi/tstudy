
# SQL 첫걸음

---

## Chapter 01. 데이터베이스와 SQL

### 01강. 데이터베이스
### 02강. 다양한 데이터베이스
### 03강. 데이터베이스 서버

---

## Chapter 02. 테이블에서 데이터 검색

### <a href="Chapter 02. 테이블에서 데이터 검색/04강. Hello World 실행하기.md" target="_blank">04강. Hello World 실행하기</a>
1) SELECT 명령 구문
2) 예약어, 데이터베이스 객체
3) 테이블, 데이터 타입
4) NULL == 값이 정해지지 않음
### <a href="Chapter 02. 테이블에서 데이터 검색/05강. 테이블 구조 참조하기.md" target="_blank">05강. 테이블 구조 참조하기</a>
1) DESC 명령과 테이블 구조
2) 데이터 타입
### <a href="Chapter 02. 테이블에서 데이터 검색/06강. 검색 조건 지정하기.md" target="_blank">06강. 검색 조건 지정하기</a>
1) SELECT 구에서 열 지정하기
2) WHERE 구에서 행 지정하기
3) 리터럴의 비교
4) NULL 값 검색
5) 비교 연산자

### <a href="Chapter 02. 테이블에서 데이터 검색/07강. 조건 조합하기.md" target="_blank">07강. 조건 조합하기</a>
1) AND
2) OR
3) 리터럴은 조건식이 아니고, 항상 참으로 처리된다.
4) 연산자의 우선순위
5) NOT
### <a href="Chapter 02. 테이블에서 데이터 검색/08강. 패턴 매칭에 의한 검색.md" target="_blank">08강. 패턴 매칭에 의한 검색</a>
1) LIKE 패턴
2) LIKE 문에서 `%` 이스케이프
3) 문자열 상수 `'` 이스케이프

---

## Chapter 03. 정렬과 연산

### <a href="Chapter 03. 정렬과 연산/09강. 정렬 - ORDER BY.md" target="_blank">09강. 정렬 - ORDER BY</a>
1) ORDER BY : 검색 결과 정렬
2) ORDER BY ~ DESC : 내림차순 정렬
3) 정렬 기준 : 값의 대소관계
4) ORDER BY는 테이블에 영향을 주지 않음

### <a href="Chapter 03. 정렬과 연산/10강. 복수의 열을 지정해 정렬하기.md" target="_blank">10강. 복수의 열을 지정해 정렬하기</a>
1) 복수의 열로 정렬 지정
2) 정렬 방법 지정하기
3) NULL 값의 정렬순서

### <a href="Chapter 03. 정렬과 연산/11강. 결과 행 제한하기 - LIMIT.md" target="_blank">11강. 결과 행 제한하기 - LIMIT</a>
1) 결과 행 제한하기 - LIMIT
2) LIMIT는 SQL 표준이 아니다.
3) 오프셋 지정

### <a href="Chapter 03. 정렬과 연산/12강. 수치 연산.md" target="_blank">12강. 수치 연산</a>
1) 사칙 연산
2) SELECT 구로 연산하기
3) 열의 별명(alias)
4) WHERE 구에서 연산하기
5) NULL 값의 연산
6) ORDER BY 구에서 연산하기
7) 함수
8) ROUND 함수
9) 그 외

### <a href="Chapter 03. 정렬과 연산/13강. 문자열 연산.md" target="_blank">13강. 문자열 연산</a>
1) 문자열 결합(CONCAT,||,+)
2) 문자열 추출(SUBSTRING)
3) 앞 뒤 공백 제거(TRIM)
4) 문자열 길이(CHARACTER_LENGTH, OCTET_LENGTH)

### <a href="Chapter 03. 정렬과 연산/14강. 날짜 연산.md" target="_blank">14강. 날짜 연산</a>
1) SQL에서의 날짜/시각
2) 시스템 날짜/시각 확인
3) 날짜/시각 서식 함수
4) 날짜/시각의 덧셈과 뺄셈

### <a href="Chapter 03. 정렬과 연산/15강. CASE문으로 데이터 변환하기.md" target="_blank">15강. CASE문으로 데이터 변환하기</a>
1) 기본 CASE문(조건식 상세 기술)
2) 또 다른 CASE문(단순 CASE문)
3) CASE를 사용할 경우 주의사항
4) COALESCE
5) NULLIF
6) 그 외 비표준 조건식

---

## Chapter 04. 데이터의 추가, 삭제, 갱신

### <a href="Chapter 04. 데이터의 추가, 삭제, 갱신/16강. 행 추가하기 - INSERT.md" target="_blank">16강. 행 추가하기 - INSERT</a>
1) INSERT로 행 추가하기
2) 값을 저장할 칼럼 지정하기
3) DEFAULT
4) NULL 삽입 주의 - NOT NULL 제약 조건
5) (MySQL) 복수의 행을 한번에 INSERT하기(Multi Row Insert)
6) 다른 테이블에서 복사하기

### <a href="Chapter 04. 데이터의 추가, 삭제, 갱신/17강. 삭제하기 - DELETE.md" target="_blank">17강. 삭제하기 - DELETE</a>
1) DELETE문
2) 조건을 지정하지 않으면 모든 행이 제거된다.


### <a href="Chapter 04. 데이터의 추가, 삭제, 갱신/18강. 데이터 갱신하기 - UPDATE.md" target="_blank">18강. 데이터 갱신하기 - UPDATE</a>
1) UPDATE로 데이터 갱신하기
2) SET 구에서의 `=`은 대입연산자
3) 복수의 열 동시 갱신
4) 복수의 열 갱신 시 실행 순서
5) DEFAULT 갱신
6) NULL 갱신

### 19강. 물리삭제와 논리삭제

---

## Chapter 05. 집계와 서브쿼리
### 20강. 행 개수 구하기 - COUNT
### 21강. COUNT 이외의 집계함수
### 22강. 그룹화 - GROUP BY
### 23강. 서브쿼리
### 24강. 상관 서브쿼리

---

## Chapter 06. 데이터베이스 객체 작성과 삭제
### 25강. 데이터베이스 객체
### 26강. 테이블 작성, 삭제, 변경
### 27강. 제약
### 28강. 인덱스 구조
### 29강. 인덱스 작성과 삭제
### 30강. 뷰 작성과 삭제

---

## Chapter 07. 복수의 테이블 다루기
### 31강. 집합 연산
### 32강. 테이블 결합
### 33강. 관계형 모델

---

## Chapter 08. 데이터베이스 설계
### 34강. 데이터베이스 설계
### 35강. 정규화
### 36강. 트랜잭션

---

## 부록A MySQL 설치

---
