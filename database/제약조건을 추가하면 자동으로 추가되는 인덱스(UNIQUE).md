# 제약조건을 추가하면 자동으로 추가되는 인덱스(UNIQUE)

---

### 테이블 생성
```mysql
DROP TABLE IF EXISTS members; -- 기존 테이블이 존재한다면 삭제

CREATE TABLE members (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) UNIQUE
);
```
- name 칼럼에 unique 제약조건을 추가했다.

---

### 인덱스 목록 조회
```sql
mysql> SHOW INDEX FROM members;
+---------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+------------+
| Table   | Non_unique | Key_name | Seq_in_index | Column_name | Collation | Cardinality | Sub_part | Packed | Null | Index_type | Comment | Index_comment | Visible | Expression |
+---------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+------------+
| members |          0 | PRIMARY  |            1 | id          | A         |           0 |     NULL |   NULL |      | BTREE      |         |               | YES     | NULL       |
| members |          0 | name     |            1 | name        | A         |           0 |     NULL |   NULL | YES  | BTREE      |         |               | YES     | NULL       |
+---------+------------+----------+--------------+-------------+-----------+-------------+----------+--------+------+------------+---------+---------------+---------+------------+
2 rows in set (0.00 sec)
```

- name 칼럼에 대응되는 인덱스가 생성됐다.
- name 기준으로도 정렬되기 때문에 name 조회가 향상될 것이다.

---
