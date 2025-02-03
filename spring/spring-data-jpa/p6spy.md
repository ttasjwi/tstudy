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
    p6-spy:
      enable-logging: true
```

#### 포맷 전략
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
- [Reference](https://www.inflearn.com/community/questions/1032603/p6spy-%ED%8F%AC%EB%A7%B7-%EC%84%A4%EC%A0%95-%EA%B3%B5%EC%9C%A0%ED%95%A9%EB%8B%88%EB%8B%A4)

---

