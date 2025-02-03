# Querydsl

---

### Querydsl
- JPA/MongoDB/SQL 등의 기술들을 위해 type-safe SQL을 만들어주는 프레임워크
  - 주로 많이 사용되는 것은 JPA 를 위한 querydsl
- JPQL 동적 쿼리 작성을 편리하게 할 수 있음
- 쿼리를 Java 코드를 통해 작성할 수 있기 때문에, 컴파일 타임에 문법 오류를 체크할 수 있다.

---

### JPA 의 한계
- 동적쿼리 작성이 힘들다.
    ```kotlin
    val sql = """
    SELECT *
    FROM member
    WHERE name like ?
    AND age BETWEEN ? AND ?
    """ 
    ```

- Query 는 결국 문자열인만큼 타입 체크가 불가능하다.
  - 실행하기 전까지는 작동여부를 확인하는 것이 불가능하다. (물론 테스트코드를 잘 작성하면 해결할 수 있는 부분도 있기는 하다)

---

### Querydsl 를 사용하면
```kotlin
val queryFactory = JPAQueryFactory(entityManager)

val m = QMember.member

val list = query
    .select(m)
    .from(m)
    .where(
        m.age.between(20,40).and(m.name.like("김%"))
    )
    .orderBy(m.age.desc())
    .limit(3)
    .fetch()
```
- 복잡한 쿼리, 동적 쿼리 작성을 편리하게 할 수 있다.
- Java 코드이므로 Jpql 문법적 오류를 컴파일 단계 수준에서 체크할 수 있다.
- 단점 및 한계
  - `Qxxx` 코드 생성을 위한 Annotation Processor 등 설정을 추가적으로 해야하는 설정의 진입 장벽이 있다.
  - JPQL 로 해결하기 어려운 Native SQL 은 JdbcTemplate, MyBatis 를 활용할 것

---
