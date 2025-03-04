# Redis 란, Redis의 장점

---

### Redis 란?
> Remote Dictionary Server의 약자로서, "키-값" 구조의 비정형 데이터를 저장하고 관리하기 위한
> 오픈 소스 기반의 비관계형 데이터베이스 관리 시스템(DBMS)이다. (위키백과)


- **데이터 처리 속도가 엄청 빠른 NoSQL 데이터베이스**
- Key-Value 형태로 데이터를 저장하는 데이터베이스
  ![what-is-redis.png](./imgs/what-is-redis.png)
  
---

### Redis 의 장점
Redis는 다양한 장점을 가지고 있다. 여러 특징 중 딱 1가지만 확실하게 기억하라.

> 레디스(Redis)는 인메모리(in-memory)에 모든 데이터를 저장한다.
그래서 데이터의 처리 성능이 굉장히 빠르다.


- MySQL과 같은 RDBMS의 데이터베이스는 대부분 디스크(Disk)에 데이터를 저장한다. 
- 하지만 Redis는 메모리(RAM)에 데이터를 저장한다. 디스크(Disk)보다 메모리(RAM)에서의 데이터 처리속도가 월등하게 빠르다. 
- 이 때문에 Redis의 데이터 처리 속도가 RDBMS에 비해 훨씬 빠르다.

---
