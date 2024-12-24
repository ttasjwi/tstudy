# CTE(Common Table Expression) - WITH 와 WITH RECURSIVE

---

### CTE 란
- Common Table Expression
- 이름을 가진 임시테이블
- SQL 문장 내에서 한 번 이상 사용될 수 있고, SQL 문장이 실행되면 자동으로 CTE 임시 테이블 역시 삭제된다.
- 위치
  - SELECT, UPDATE, DELETE 문장의 제일 앞쪽
    - `WITH cte1 AS (SELECT ...) SELECT ...`
    - `WITH cte1 AS (SELECT ...) UPDATE ...`
    - `WITH cte1 AS (SELECT ...) DELETE ...`
  - 서브쿼리의 제일 앞쪽
    - `SELECT ... FROM WHERE id IN (WITH cte1 AS (SELECT ...) SELECT ...) ...`
    - `SELECT ... FROM (WITH cte1 AS (SELECT ...) SELECT ...) ...`
  - SELECT 절의 바로 앞 쪽
    - `INSERT WITH cte AS (SELECT ...) SELECT ...`
    - `REPLACE ... WITH cte1 AS (SELECT ...) SELECT ...`
    - `CREATE TABLE ... WITH cte AS (SELECT ...) SELECT ...`
    - `CREATE VIEW ... WITH cte AS (SELECT ...) SELECT ...`
    - `DECLARE CURSOR ... WITH cte AS (SELECT ...) SELECT ...`
    - `EXPLAIN ... WITH cte AS (SELECT ...) SELECT ...`

---

### 비 재귀적 CTE
```sql
-- cte1 이름으로 임시테이블을 선언하고 재사용
WITH cte1 AS (SELECT * FROM departments)
SELECT * FROM cte1
```
```sql
-- 동일한 작동을 하는 쿼리.
SELECT *
FROM (SELECT * FROM departments) cte1
```
- cte 쿼리는 WITH 절로 정의하고, 이후 실행될 쿼리에서 cte 쿼리를 재사용할 수 있다.
- 이 두 쿼리 작동은 실행 계획을 통해 확인하면 동일하게 작동한다.
- 결론
  - CTE 임시 테이블은 재사용 가능하므로 FROM 절 서브쿼리보다 효율적이다
  - CTE 로 선언된 임시 테이블을 다른 CTE 쿼리에서 참조할 수 있다.
  - CTE 는 임시 테이블의 생성 부분과 사용 부분의 코드를 분리할 수 있으므로 가독성이 높다.

---

### 재귀적 CTE
```sql
WITH RECURSIVE cte (no) AS (
    SELECT 1 -- 비 재귀적 파트
    UNION ALL
    SELECT (no + 1) FROM cte WHERE no < 5 -- 재귀적 파트 (쿼리 결과가 없을 때까지 반복 실행)
)
```
```shell
1 # 비재귀
1,2 # 재귀
1,2,3
1,2,3,4
1,2,3,4,5 # 종료
```
- 실행순서
  - 비 재귀적 파트 실행 후 그 결과를 기반으로 cte 이름의 임시 테이블생성 및 저장
  - 위의 결과를 입력으로 사용해 재귀적 파트의 쿼리를 실행
  - 위의 결과를 cte 임시 테이블에 저장 (UNION 또는 UNION DISTINCT 의 경우 중복 제거 실행, UNION ALL 에는 중복 허용)
  - 위의 결과를 입력으로 사용해 재귀적 파트의 쿼리를 실행
  - 쿼리 결과가 없을 때까지 반복...

```sql
-- 최대 재귀 호출 횟수를 제한
SET cte_max_recursion_depth = 10;
```
- 재귀적 cte 실행 전, 최대 재귀 호출 횟수 제한값을 걸어 혹시 모를 불상사를 방지할 수 있음.
- 최대 재귀호출 횟수 제한을 초과할 경우 에러 발생

---

### 재귀적 CTE 활용
- 반복적으로 다량의 데이터 삽입
- 연결리스트형 자료
  - 예) 상위 조직장 계층을 테이블로 조회하기, ...


---

- Reference : Real MySQL 8.0 (11.4 장)

---
