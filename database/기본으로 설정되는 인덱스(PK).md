# 기본으로 설정되는 인덱스(PK)

---

### 테이블 생성
```sql
DROP TABLE IF EXISTS members; # 기존 테이블이 존재하면 삭제

CREATE TABLE members (
                       id INT PRIMARY KEY,
                       name VARCHAR(100)
);
```

---

### 데이터 삽입 후 조회
```sql
INSERT INTO members (id, name) VALUES
                                 (1, 'a'),
                                 (3, 'b'),
                                 (5, 'c'),
                                 (7, 'd');

SELECT * FROM members;
```
```bash
mysql> select * from members;
+----+------+
| id | name |
+----+------+
|  1 | a    |
|  3 | b    |
|  5 | c    |
|  7 | d    |
+----+------+
4 rows in set (0.00 sec)
```
- 데이터를 조회해보면 id (1,3,5,7) 순으로 조회된다

---

### id 수정
```sql
UPDATE members
SET id = 2
WHERE id = 7;

SELECT * FROM members;
```

---

### 조회
```sql
mysql> SELECT * FROM members;
+----+------+
| id | name |
+----+------+
|  1 | a    |
|  2 | d    |
|  3 | b    |
|  5 | c    |
+----+------+
4 rows in set (0.00 sec)
```
- 다시 조회해보면 1,2,3,5 순으로 조회된다.
- 사실 내부적으로 PK 에 해당하는 인덱스가 생성되어 있고 이 인덱스를 사용하여 조회했기 때문에 이런 결과가 나온 것을 추측할 수 있다.
  - 지금 사용하고 있는 데이터베이스는 MySQL 인데, 대부분의 관계형 데이터베이스 테이블들은 이렇게 프라이머리 키(클러스터링 인덱스)를 기준으로 클러스터링되어 저장된다.
- 반드시 PK 순으로 조회되는 것이 중요하다면 ORDER BY 를 명시적으로 붙여서 조회하자.

---

### 실제 인덱스 확인
```sql
mysql> SHOW INDEX FROM members;
+---------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+------------+
| Table   | Non_unique | Key_name | Seq_in_index | Column_name | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment | Visible | Expression |
+---------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+------------+
| members |          0 | PRIMARY  |            1 | id          | A         |           4 |     NULL |   NULL |      | BTREE      |         |               | YES     | NULL       |
+---------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+------------+
1 row in set (0.01 sec)
```
- 실제 members 테이블에는 PRIMARY 인덱스가 하나 존재한다. id 칼럼을 기준으로 클러스터링되어 정렬되어 있다.

---
