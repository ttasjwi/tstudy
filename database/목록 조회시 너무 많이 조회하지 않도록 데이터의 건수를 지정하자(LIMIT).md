# 목록 조회시 너무 많이 조회하지 않도록 데이터의 건수를 지정하자(LIMIT)

---

### 1. 예시(LIMIT 없이)

#### 1.1 테이블 생성
```mysql
DROP TABLE IF EXISTS users; # 기존 테이블 삭제

CREATE TABLE users (
                       id INT AUTO_INCREMENT PRIMARY KEY,
                       name VARCHAR(100),
                       age INT
);
```

#### 1.2 데이터 삽입
```mysql
-- 높은 재귀(반복) 횟수를 허용하도록 설정
-- (아래에서 생성할 더미 데이터의 개수와 맞춰서 작성하면 된다.)
SET SESSION cte_max_recursion_depth = 1000000;

-- 더미 데이터 삽입 쿼리
INSERT INTO users (name, age)
WITH RECURSIVE cte (n) AS
                   (
                       SELECT 1
                       UNION ALL
                       SELECT n + 1 FROM cte WHERE n < 1000000 -- 생성하고 싶은 더미 데이터의 개수
                   )
SELECT
    CONCAT('User', LPAD(n, 7, '0')),   -- 'User' 다음에 7자리 숫자로 구성된 이름 생성
    FLOOR(1 + RAND() * 1000) AS age    -- 1부터 1000 사이의 난수로 나이 생성
FROM cte;
```

#### 1.3 데이터 조회
```shell
SELECT * FROM users;
>> 1,000,000 rows retrieved starting from 1 in 3 s 898 ms (execution: 5 ms, fetching: 3 s 893 ms)
```
- LIMIT 없이 데이터를 조회하면 `3898ms` 가 소요된다. (100만 건 조회)
- 이렇게 조회하는 속도도 문제지만 데이터가 1000만, 1억건 이렇게 되는 데이터를 메모리에 가져오면 java 기준 OutOfMemoryError 가 발생할 수 도 있다.
- 적절한 선에서 데이터 건수를 줄여서 조회하는 방식을 써야한다.

---

### 2. 조회 결과의 데이터 갯수를 줄여라
```shell
SELECT * FROM users LIMIT 10;
>> 10 rows retrieved starting from 1 in 354 ms (execution: 5 ms, fetching: 349 ms)
```
- 실제 대부분 온라인 서비스들은 페이지네이션을 적용하여, 필요한 부분 데이터들을 그 때 그 때 조회하는 방식이다.
- 그 이유는 조회하는 데이터의 갯수가 성능에 많은 영향을 끼치기 때문이다.
- **데이터를 조회할 때 한 번에 너무 많은 데이터를 조회하는 건 아닌 지 체크해봐라.**
- **`LIMIT`, `WHERE`문 등을 활용해서 한 번에 조회하는 데이터의 수를 줄이는 방법을 고려해봐라.**

---
