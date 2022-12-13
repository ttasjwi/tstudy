
# Core Spring Security

인프런 정수원 님의 [스프링 시큐리티 - Spring Boot 기반으로 개발하는 Spring Security](https://www.inflearn.com/course/%EC%BD%94%EC%96%B4-%EC%8A%A4%ED%94%84%EB%A7%81-%EC%8B%9C%ED%81%90%EB%A6%AC%ED%8B%B0)

---

## Chapter 01. 스프링 시큐리티 기본 API 및 Filter 이해
### <a href="Chapter 01. 스프링 시큐리티 기본 API 및 Filter 이해/1.01 프로젝트 구성 및 의존성 추가.md" target="_blank">1.01 프로젝트 구성 및 의존성 추가</a>
1) 프로젝트 생성
2) IDE 설정(IntelliJ)
3) Gradle 설정
4) 테스트 컨트롤러 생성
5) 스프링 시큐리티 의존성 추가 시 일어나는 일들
6) 스프링 시큐리티 기본 제공 기능의 한계

### <a href="Chapter 01. 스프링 시큐리티 기본 API 및 Filter 이해/1.02 사용자 정의 보안 기능 구현.md" target="_blank">1.02 사용자 정의 보안 기능 구현</a>
1) WebSecurityConfigurerAdapter
2) HttpSecurity : 보안 설정 편의 API 제공
3) 사용자 정의 보안 기능 구현하기
4) 디폴트 자격증명 사용자 id, password 지정

### <a href="Chapter 01. 스프링 시큐리티 기본 API 및 Filter 이해/1.03 Form Login 인증.md" target="_blank">1.03 Form Login 인증</a>
1) Form Login 흐름
2) Form Login 관련 스프링 시큐리티 API

### <a href="Chapter 01. 스프링 시큐리티 기본 API 및 Filter 이해/1.04 Form Login 인증 필터 - UsernamePasswordAuthenticationFilter.md" target="_blank">1.04 Form Login 인증 필터 - UsernamePasswordAuthenticationFilter</a>
1) Form Login 인증 - 필터 흐름

### <a href="Chapter 01. 스프링 시큐리티 기본 API 및 Filter 이해/1.05 Logout 처리, LogoutFilter.md" target="_blank">1.05 Logout 처리, LogoutFilter</a>
1) Logout 흐름
2) Logout 관련 스프링 시큐리티 API
3) LogoutFilter 흐름

### <a href="Chapter 01. 스프링 시큐리티 기본 API 및 Filter 이해/1.06 Remember Me 인증.md" target="_blank">1.06 Remember Me 인증</a>
1) Remember Me 인증
2) Remember Me 인증 관련 스프링 시큐리티 API


### <a href="Chapter 01. 스프링 시큐리티 기본 API 및 Filter 이해/1.07 Remember Me 인증 필터 - RememberMeAuthenticationFilter.md" target="_blank">1.07 Remember Me 인증 필터 - RememberMeAuthenticationFilter</a>
1) Remember Me 인증 필터 통작 방식

### <a href="Chapter 01. 스프링 시큐리티 기본 API 및 Filter 이해/1.08 익명사용자 인증 필터 - AnonymousAuthenticationFilter.md" target="_blank">1.08 익명사용자 인증 필터 - AnonymousAuthenticationFilter</a>
1) AnonymousAuthenticationFilter
2) 익명 사용자의 Authentication은 어디에도 갈 수 없는 통행증
3) 익명 객체는 세션에 저장하지 않는다.
4) 소스 코드로 확인하기

### 1.09 동시 세션 제어, 세션 고정 보호, 세션 정책
### 1.10 세션 제어 필터 : SessionManagementFilter, ConcurrentSessionFilter
### 1.11 권한설정과 표현식
### 1.12 예외 처리 및 요청 캐시 필터 : ExceptionTranslationFilter, RequestCacheAwareFilter
### 1.13 사이트 간 요청 위조 - CSRF, CsrfFilter

---

## Chapter 02. 스프링 시큐리티 주요 아키텍처 이해
### 2.01 위임 필터 및 필터 빈 초기화 - DelegatingProxyChain, FilterChainProxy
### 2.02 필터 초기화와 다중 보안 설정
### 2.03 인증 개념 이해 - Authentication
### 2.04 인증 저장소 - SecurityContextHolder, SecurityContext
### 2.05 인증 저장소 필터 - SecurityContextPersistenceFilter
### 2.06 인증 흐름 이해 - Authentication Flow
### 2.07 인증 관리자 : AuthenticationManager
### 2.08 인증 처리자 - AuthenticationProvider
### 2.09 인가 개념 및 필터 이해 : Authorization, FilterSecurityInterceptor
### 2.10 인가 결정 심의자 - AccessDecisionManager, AccessDecisionVoter
### 2.11 스프링 시큐리티 필터 및 아키텍처 정리

---

## Chapter 03. 실전프로젝트 - 인증 프로세스 Form 인증 구현
### 3.01 실전 프로젝트 생성
### 3.02 정적 자원 관리 - WebIgnore 설정
### 3.03 사용자 DB 등록 및 PasswordEncoder
### 3.04 DB 연동 인증 처리(1) : CustomUserDetailsService
### 3.05 DB 연동 인증 처리(2) : CustomAuthenticationProvider
### 3.06 커스텀 로그인 페이지 생성하기
### 3.07 로그아웃 및 인증에 따른 화면 보안 처리
### 3.08 인증 부가 기능 - WebAuthenticationDetails, AuthenticationDetailsSource
### 3.09 인증 성공 핸들러 : CustomAuthenticationSuccessHandler
### 3.10 인증 실패 핸들러 : CustomAuthenticationFailureHandler
### 3.11 인증 거부 처리 - Access Denied

---

## Chapter 04. 실전프로젝트 - 인증 프로세스 Ajax 인증 구현
### 4.1 흐름 및 개요
### 4.2 인증 필터 - AjaxAuthenticationFilter
### 4.3 인증 처리자 - AjaxAuthenticationProvider
### 4.4 인증 핸들러 - AjaxAuthenticationSuccessHandler, AjaxAuthenticationFailureHandler
### 4.5 인증 및 인가 예외 처리 - AjaxLoginUrlAuthenticationEntryPoint, AjaxAccessDeniedHandler
### 4.6 Ajax Custom DSLs 구현하기
### 4.7 Ajax 로그인 구현 & CSRF 설정

---

## Chapter 05. 실전프로젝트 - 인가 프로세스 DB 연동 웹 계층 구현
### 5.1 스프링 시큐리티 인가 개요
### 5.2 관리자 시스템 - 권한 도메인, 서비스, 리포지토리 구성
### 5.3 웹 기반 인가처리 DB 연동 - 주요 아키텍처 이해
### 5.4 웹 기반 인가처리 DB 연동 - FilterInvocationSecurityMetadataSource (1)
### 5.5 웹 기반 인가처리 DB 연동 - FilterInvocationSecurityMetadataSource (2)
### 5.6 웹 기반 인가처리 실시간 반영하기
### 5.7 인가처리 허용 필터 - PermitAllFilter 구현
### 5.8 계층 권한 적용하기- RoleHierarchy
### 5.9 아이피 접속 제한하기 - CustomIpAddressVoter

---

## Chapter 06. 실전프로젝트 - 인가 프로세스 DB 연동 서비스 계층 구현
### 6.1 Method 방식 개요
### 6.2 어노테이션 권한 설정 - @PreAuthorize, @PostAuthorize, @Secured, @RolesAllowed
### 6.3 AOP Method 기반 DB 연동 - 주요 아키텍처 이해
### 6.4 AOP Method 기반 DB 연동 - MapBasedSecurityMetadataSource (1)
### 6.5 AOP Method 기반 DB 연동 - MapBasedSecurityMetadataSource (2)
### 6.6 AOP Method 기반 DB 연동 - MapBasedSecurityMetadataSource (3)
### 6.7 AOP Method 기반 DB 연동 - ProtectPointcutPostProcessor

---

## Chapter 07. 번외편 - 메소드 보안 실시간 DB 연동 구현
### 7.1 ProxyFactory 를 활용한 실시간 메소드 보안 구현

---
