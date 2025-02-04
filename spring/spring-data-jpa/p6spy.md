# p6spy

---

### p6spy 란?
- `Datasource` 를 한 단계 더 데코레이팅하여, 중간단계에서 작성되는 로그를 포맷팅하기 편하게 만들어주는 라이브러리
- 구체적인 파라미터를 로그에 직접 넣어서 볼 수 있게 해준다.

---

### Hibernate 로깅 방식의 한계
- hibernate 로깅 방식은 SQL 실행 파라미터를 로그로 남기지 못 한다.

---

### 설정방법

#### build.gradle.kts
```kotlin
dependencies {
    implementation("com.github.gavlyukovskiy:p6spy-spring-boot-starter:1.10.0")
}
```
- 공식 github 리포지토리: https://github.com/gavlyukovskiy/spring-boot-data-source-decorator
  - 현재 major 버전은 리포지토리에서 게시되어 있으므로 참고해서 변경할 것

#### application.yml 추가
```yaml
logging:
  level:
    p6spy: info # p6spy 로깅 레벨

decorator:
  datasource:
    p6spy:
      enable-logging: true
```

#### 포맷 전략 및 이벤트 리스너
[Reference](https://www.inflearn.com/community/questions/1032603/p6spy-%ED%8F%AC%EB%A7%B7-%EC%84%A4%EC%A0%95-%EA%B3%B5%EC%9C%A0%ED%95%A9%EB%8B%88%EB%8B%A4)


```kotlin
package hello.querydsl.config

import com.p6spy.engine.logging.Category
import com.p6spy.engine.spy.appender.MessageFormattingStrategy
import org.hibernate.engine.jdbc.internal.FormatStyle
import org.springframework.stereotype.Component

@Component
class P6SpyFormattingStrategy : MessageFormattingStrategy {

    companion object {
        private const val NEW_LINE = "\n"
        private const val TAP = "\t"
        private val DDL_COMMANDS = listOf("create", "alter", "drop", "comment")
    }

    override fun formatMessage(
        connectionId: Int,
        now: String,
        elapsed: Long,
        category: String,
        prepared: String,
        sql: String,
        url: String
    ): String {
        if (sql.trim().isEmpty()) {
            return formatByCommand(category)
        }
        return formatBySql(sql, category) + getAdditionalMessages(elapsed)
    }

    private fun formatByCommand(category: String): String {
        return (NEW_LINE
                + "Execute Command : "
                + NEW_LINE
                + NEW_LINE
                + TAP
                + category
                + NEW_LINE
                + NEW_LINE
                + "----------------------------------------------------------------------------------------------------")
    }

    private fun formatBySql(sql: String, category: String): String {
        return if (isStatementDDL(sql, category)) {
            (NEW_LINE
                    + "Execute DDL : "
                    + NEW_LINE
                    + FormatStyle.DDL
                .formatter
                .format(sql))
        } else {
            (NEW_LINE
                    + "Execute DML : "
                    + NEW_LINE
                    + FormatStyle.BASIC
                .formatter
                .format(sql))
        }
    }

    private fun getAdditionalMessages(elapsed: Long): String {
        return (NEW_LINE
                + NEW_LINE
                + String.format("Execution Time: %s ms", elapsed) + NEW_LINE
                + "----------------------------------------------------------------------------------------------------")
    }

    private fun isStatementDDL(sql: String, category: String): Boolean {
        return isStatement(category) && isDDL(sql.trim().lowercase())
    }

    private fun isStatement(category: String): Boolean {
        return Category.STATEMENT.name == category
    }

    private fun isDDL(lowerSql: String): Boolean {
        return DDL_COMMANDS.any { lowerSql.startsWith(it) }
    }

}
```
- 포맷팅을 담당하는 전략. P6SPY 내부적으로 이 설정 파일을 참조하여 SQL 메시지를 커스텀하게 포맷팅해준다.

```kotlin
package hello.querydsl.config

import com.p6spy.engine.common.ConnectionInformation
import com.p6spy.engine.event.JdbcEventListener
import com.p6spy.engine.spy.P6SpyOptions
import org.springframework.stereotype.Component
import java.sql.SQLException

@Component
class P6SpyEventListener : JdbcEventListener() {

    override fun onAfterGetConnection(connectionInformation: ConnectionInformation?, e: SQLException?) {
        P6SpyOptions.getActiveInstance().logMessageFormat = P6SpyFormattingStrategy::class.java.getName()
    }
}
```
- 커넥션 획득 시에도 P6SPY 포맷팅이 적용될 수 있도록 P6Spy 이벤트 리스너 설정을 추가로 작성

---

### 실행 확인


#### 샘플 Entity
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

#### DDL 실행
```shell
2025-02-04T10:05:37.468+09:00  INFO 23496 --- [querydsl] [           main] p6spy                                    : 
Execute DDL : 

    drop table if exists hello

Execution Time: 16 ms
----------------------------------------------------------------------------------------------------
2025-02-04T10:05:37.495+09:00  INFO 23496 --- [querydsl] [           main] p6spy                                    : 
Execute DDL : 

    create table hello (
        id bigint not null auto_increment,
        primary key (id)
    ) engine=InnoDB

Execution Time: 21 ms
----------------------------------------------------------------------------------------------------
```
- 최초 DDL 실행시(ddl-auto: create 기준) 포맷팅된 SQL 이 출력되는 것을 볼 수 있다.

#### DML 파라미터 확인
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
            .where(qHello.id.eq(hello.id))
            .fetchOne()!!

        assertThat(result).isEqualTo(hello)
        assertThat(result.id).isEqualTo(hello.id)
    }

}
```
```shell
2025-02-04T10:13:15.421+09:00  INFO 2624 --- [querydsl] [    Test worker] p6spy                                    : 
Execute DML : 

    insert 
    into
        hello
        
    values
        ( )

Execution Time: 2 ms
----------------------------------------------------------------------------------------------------
2025-02-04T10:13:16.002+09:00  INFO 2624 --- [querydsl] [    Test worker] p6spy                                    : 
Execute DML : 

    select
        h1_0.id 
    from
        hello h1_0 
    where
        h1_0.id=1

Execution Time: 6 ms
----------------------------------------------------------------------------------------------------
```
- DML 실행 과정에서 파라미터 자리에, 구체값이 포함되어 로깅되는 것을 볼 수 있다.

---
