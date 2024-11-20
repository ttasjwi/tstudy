# 스프링 시큐리티에 코틀린 DSL 적용하기

---

## 스프링 시큐리티 - Java DSL
자바, 순수 코틀린 문법을 사용하다보면 스프링 시큐리티 필터체인을 작성할 때 다음과 같이 작성해야한다.

```java
	@Bean
	public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
		http
			.authorizeHttpRequests((authorize) -> authorize
				.requestMatchers("/login").permitAll()
				.anyRequest().authenticated()
			);

		return http.build();
	}
```
물론 이것도 괜찮긴 한데, 람다 표현식을 체이닝을 통해 넣어주는 식이기도 하고 가독성이 썩 좋지는 않다.

---

## 스프링 시큐리티 - Kotlin DSL
```kotlin
import org.springframework.security.config.annotation.web.invoke
```
- 코틀린을 쓴다면 이 import 문을 Security 관련 Config 클래스 파일에 삽입해보자.
- IDE의 지원을 받아서 자동 작성할 수 없다보니, 개발자가 수동으로 import문을 넣어줘야한다.
- 자주 사용한다면 IntelliJ의 Live Template 에 추가해서 사용하는 것도 괜찮은 선택이 될 수 있다.

```kotlin
    @Bean
    @Order(0)
    fun ajaxSecurityFilterChain(http: HttpSecurity): SecurityFilterChain {
        http {
            securityMatcher("/api/**", "/admin/api/**")
            authorizeHttpRequests {
                authorize("/admin/api/**", hasRole("ADMIN"))
                authorize("/api/login", permitAll)
                authorize("/api/users", permitAll)
                authorize("/api/messages", hasRole("MANAGER"))
                authorize(anyRequest, authenticated)
            }
            addFilterBefore<UsernamePasswordAuthenticationFilter>(ajaxLoginProcessingFilter())
            exceptionHandling {
                authenticationEntryPoint = ajaxAuthenticationEntryPoint()
                accessDeniedHandler = ajaxAccessDeniedHandler()
            }
        }
        return http.build()
    }
```
- 위의 내용을 import하면, 스프링 시큐리티를 위한 DSL을 사용할 수 있게 되고, 위와 같이 시큐리티 설정 코드를 작성할 수 있게 된다.
- 순수 java, kotlin 문법을 사용하면 설정 클래스 가독성이 개인적으로 좋아보이지 않았는데, 개인적으로는 이쪽을 쓰는게 가독성에서 더 좋다.

```kotlin
    fun authorizeRequests(authorizeRequestsConfiguration: AuthorizeRequestsDsl.() -> Unit) {
        val authorizeRequestsCustomizer = AuthorizeRequestsDsl().apply(authorizeRequestsConfiguration).get()
        this.http.authorizeRequests(authorizeRequestsCustomizer)
    }
```

- 참고로 여기서 authorizeHttpRequests 와 같은 부분을 IntelliJ에서 Ctrl + 클릭을 통해 해당 코드를 따라가보면 이런 코드를 확인할 수 있는데, 
AuthorizeRequestDsl을 Ctrl+클릭해보자.

```kotlin
/**
 * A Kotlin DSL to configure [HttpSecurity] request authorization using idiomatic Kotlin code.
 *
 * @author Eleftheria Stein
 * @since 5.3
 */
class AuthorizeRequestsDsl : AbstractRequestMatcherDsl() {
    private val authorizationRules = mutableListOf<AuthorizationRule>()

    private val HANDLER_MAPPING_INTROSPECTOR_BEAN_NAME = "mvcHandlerMappingIntrospector"
    private val HANDLER_MAPPING_INTROSPECTOR = "org.springframework.web.servlet.handler.HandlerMappingIntrospector"
    private val MVC_PRESENT = ClassUtils.isPresent(
            HANDLER_MAPPING_INTROSPECTOR,
            AuthorizeRequestsDsl::class.java.classLoader)
    private val PATTERN_TYPE = if (MVC_PRESENT) PatternType.MVC else PatternType.ANT

    /**
     * Adds a request authorization rule.
     *
     * @param matches the [RequestMatcher] to match incoming requests against
     * @param access the SpEL expression to secure the matching request
     * (i.e. "hasAuthority('ROLE_USER') and hasAuthority('ROLE_SUPER')")
     */
    fun authorize(matches: RequestMatcher = AnyRequestMatcher.INSTANCE,
                  access: String) {
        authorizationRules.add(MatcherAuthorizationRule(matches, access))
    }

    /**
     * Adds a request authorization rule for an endpoint matching the provided
     * pattern.
     * If Spring MVC is on the classpath, it will use an MVC matcher.
     * If Spring MVC is not on the classpath, it will use an ant matcher.
     * The MVC will use the same rules that Spring MVC uses for matching.
     * For example, often times a mapping of the path "/path" will match on
     * "/path", "/path/", "/path.html", etc.
     * If the current request will not be processed by Spring MVC, a reasonable default
     * using the pattern as an ant pattern will be used.
     *
     * @param pattern the pattern to match incoming requests against.
     * @param access the SpEL expression to secure the matching request
     * (i.e. "hasAuthority('ROLE_USER') and hasAuthority('ROLE_SUPER')")
     */
    fun authorize(pattern: String, access: String) {
        authorizationRules.add(PatternAuthorizationRule(pattern = pattern,
                                                        patternType = PATTERN_TYPE,
                                                        rule = access))
    }
```
- 이렇게 따라가보면 DSL Api를 사용하는 방법들을 설명해놓아서 가끔 궁금해질 때 있으면 꺼내서 쓰기 좋다.

## 기술 사용 시 단점
- 스프링 시큐리티 공식 문서에서 kotlin 버전에 대한 설명은 kotlindsl로 설명되어 있기도 하고 처음에는 괜찮다고 느낀 방식이이였다.
- 하지만 쓰다보니 기술이 성숙화되지 않았다는 느낌을 받았다.
- 예를 들면 JavaDSL 방식과 다르게 동작하는 기능이 존재한다. Spring Security 6.3 기준 여러군데 존재한다. 
  - [RoleHierarchy 빈을 KotlinDSL 방식에서 사용하지 않는 문제](https://github.com/spring-projects/spring-security/issues/15136 "Support RoleHierarchy Bean in authorizeHttpRequests Kotlin DSL")
  - [GrantedAuthorityDefaults 빈을 KotlinDSL 방식에서 사용하지 않는 문제](https://github.com/spring-projects/spring-security/issues/15171 "Support GrantedAuthorityDefaults Bean in authorizeHttpRequests Kotlin DSL"))
- 반박
  - 그렇다고 KotlinDSL 방식을 무조건 버리기도 애매하다. 잘 사용되는 기능에 한해서는 코드 작성이 깔끔해지는 장점이 정말 크기 때문이다.
  - 그리고, 스프링 시큐리티 팀에서는 이런 부분에 대해서 고쳐나가려는 노력을 지속적으로 하고 계시고 그 덕에 기능들이 점점 기존 JavaDSL 을 따라가고 있다.

---

