# 트랜잭션 격리 수준(Isolation Level)

---

### 1. 트랜잭션 격리 수준에 따른 이상 현상
- Dirty Read : 커밋되기 이전의 변경된(더럽혀진) 데이터를 다른 트랜잭션에서 조회할 수 있는 현상
- Non-Repeatable Read
  - 한 트랜잭션 내에서, 다른 트랜잭션의 커밋 이전, 이후에 따라 조회결과가 달라질 수 있는 현상.
- Phantom Read
  - 한 트랜잭션 내에서, 다른 트랜잭션의 커밋 이전, 이후에 따라 추가/삭제된 레코드가 발견될 수 있는 현상

---

### 2. READ UNCOMMITTED
- Dirty Read 발생
- Non-Repeatable Read 발생
- Phantom Read 발생

---

### 3. READ COMMITTED
- Dirty Read 는 더 이상 발생하지 않음.
  - MySQL 은 이 부분을 언두로그에 백업해둔 변경 이전의 데이터를 다른 트랜잭션에서 조회하도록 한다. (MVCC)
- Non-Repeatable Read 발생
- Phantom Read 발생

---

### 4. REPEATABLE READ
- Dirty Read 발생하지 않음.
- Non-Repeatable Read 발생하지 않음.
- Phantom Read 발생하는게 일반적인데, MySQL 에서는 거의 발생하지 않음.
  - Gap Lock
    - 레코드와 레코드 사이의 갭(Gap)을 잠금
    - 트랜잭션이 특정 범위의 데이터를 읽을 경우, 그 범위의 빈 갭(Gap)에 새로운 행을 INSERT 하는 것을 막음.
    - 레코드 사이의 Gap 만 잠그므로, 기존 데이터 수정은 가능함.
  - Next-Key Lock
    - 레코드 그 자체와 그 사이의 갭(Gap)을 잠금. (Record Lock + Gap Lock)
    - 레코드 자체도 잠그므로, 레코드의 수정뿐만 아니라, 중간 삽입(INSERT)도 막게 됨.

---

### 5. SERIALIZABLE
- 여러 트랜잭션이 동일한 레코드에 동시 접근할 수 없음
- 트랜잭션이 순차적으로 진행되어야 함. 트랜잭션이 순차적으로 처리되어야 하므로 동시 처리 성능이 매우 떨어진다.

---
