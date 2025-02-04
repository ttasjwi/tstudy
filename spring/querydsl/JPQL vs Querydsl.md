# JPQL vs Querydsl

---

### 실습 환경 구성
```kotlin
@SpringBootTest
@Transactional
class QuerydslBasicTest @Autowired constructor(
    private val em: EntityManager,
) {

    private lateinit var queryFactory: JPAQueryFactory

    @BeforeEach
    fun setup() {

        // 참고로 동시성 문제는 EntityManager 수준에서 해결되기 때문에
        // JPAQueryFactory 를 필드로 관리해도 만들어도 상관은 없다.
        // 따라서 JPAQueryFactory 빈을 하나 만들어서 관리해도 상관 없다.
        queryFactory = JPAQueryFactory(em)

        val teamA = Team.create("teamA")
        val teamB = Team.create("teamB")

        em.persist(teamA)
        em.persist(teamB)

        val member1 = Member.create("member1", 10, teamA)
        val member2 = Member.create("member2", 20, teamA)
        val member3 = Member.create("member3", 30, teamB)
        val member4 = Member.create("member4", 40, teamB)

        em.persist(member1)
        em.persist(member2)
        em.persist(member3)
        em.persist(member4)
    }
}
```
- 의존성 주입 : EntityManager
- beforeEach
  - JPAQueryFactory 초기화
    - JPAQueryFactory 를 필드로 제공하면 동시성 문제가 발생하지 않을까 하는 걱정이 생길 수 있다. 그러나 동시성 문제는 EntityManager 수준에서
    해결된다. 같은 EntityManager 에 접근해도 트랜잭션마다 별도의 영속성 컨텍스트를 제공하기 때문이다.
    - 따라서 JPAQueryFactory를 빈으로 등록해서 관리해도 상관이 없다.
  - Team 엔티티, Member 엔티티 저장

---

### JPQL
```kotlin
    @Test
    fun startJPQL() {
        val jpql = """
            SELECT m
            FROM Member m
            WHERE m.username = :username
        """.trimIndent()

        val findMember = em.createQuery(jpql, Member::class.java)
            .setParameter("username", "member1")
            .singleResult

        assertThat(findMember.username).isEqualTo("member1")
    }
```
- 쿼리(JPQL)를 직접 문자열로 작성
- 파라미터 바인딩을 위해 `:username`과 같이 직접 파라미터를 지정해야한다.
- 문제가 터진다면 런타임에 문제가 발생한다.

---

### Querydsl
```kotlin
    @Test
    fun startQuerydsl() {
        val m = QMember("m")
        val findMember = queryFactory
            .select(m)
            .from(m)
            .where(m.username.eq("member1"))
            .fetchOne()!!

        assertThat(findMember.username).isEqualTo("member1")
    }
```
- 쿼리를 Java DSL 로 작성하고, 이를 토대로 JPQL 을 만들어줌
- 파라미터 바인딩을 자동으로 처리한다.
- 문제가 터진다면 컴파일 타임에 문제가 발생한다.

---
