# Querydsl 설정

---

### kotlin 설정

#### build.gradle.kts
```kotlin
plugins {
    id("org.jetbrains.kotlin.jvm") version "1.9.25"
    id("org.jetbrains.kotlin.plugin.spring") version "1.9.25"
    id("org.jetbrains.kotlin.plugin.jpa") version "1.9.25"
    id("org.jetbrains.kotlin.kapt") version "1.9.25"
    id("org.springframework.boot") version "3.4.2"
    id("io.spring.dependency-management") version "1.1.7"
}


dependencies {
    // querydsl
    implementation("com.querydsl:querydsl-jpa:5.0.0:jakarta")
    kapt("com.querydsl:querydsl-apt:5.0.0:jakarta")
}
```
- Querydsl 실행을 위한 최소한의 설정들이다. (JPA, Spring 설정 등은 기본적으로 있다는 전제 하)

#### 샘플 JpaEntity
```kotlin
package hello.querydsl.entity

import jakarta.persistence.Entity
import jakarta.persistence.GeneratedValue
import jakarta.persistence.GenerationType
import jakarta.persistence.Id

@Entity
class Hello(
    @Id @GeneratedValue(strategy = GenerationType.IDENTITY)
    var id: Long? = null
)
```
- 샘플 Entity 를 생성한다.

#### QJpaEntity 확인
```shell
./gradlew clean build
```
- gradle 명령을 사용하거나, IntelliJ 의 기능을 사용하여 프로젝트를 다시 빌드한다.
- 프로젝트 디렉토리의 `build/generated/source/kapt/main/..` 을 따라 가보면 `QHello` 가 생성되어 있는 것을 확인할 수 있다.

### 테스트코드 실행
```kotlin
@SpringBootTest
@Transactional
class QuerydslApplicationTests @Autowired constructor(
    private val em: EntityManager
) {

    @Test
    fun contextLoads() {
        val hello = Hello()
        em.persist(hello)

        val query = JPAQueryFactory(em)
        val qHello = QHello.hello

        val result: Hello = query
            .selectFrom(qHello)
            .fetchOne()!!

        assertThat(result).isEqualTo(hello)
        assertThat(result.id).isEqualTo(hello.id)
    }

}
```
```shell
Execute DML : 

    insert 
    into
        hello
        
    values
        ( )

Execution Time: 2 ms
----------------------------------------------------------------------------------------------------
2025-02-04T10:19:56.030+09:00  INFO 24120 --- [querydsl] [    Test worker] p6spy                                    : 
Execute DML : 

    select
        h1_0.id 
    from
        hello h1_0

Execution Time: 3 ms
----------------------------------------------------------------------------------------------------
```
- 쿼리문이 잘 출력되는 것을 확인하면 성공

---
