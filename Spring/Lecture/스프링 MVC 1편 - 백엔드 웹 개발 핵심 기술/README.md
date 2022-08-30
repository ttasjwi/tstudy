
# 스프링 MVC 1편 - 백엔드 웹 개발 핵심 기술

---

## Chapter 01. 웹 어플리케이션의 이해
### <a href="Chapter 01. 웹 애플리케이션의 이해/1.1 웹 서버, 웹 애플리케이션 서버.md" target="_blank">1.1 웹 서버, 웹 애플리케이션 서버</a>
1) 대부분의 모던 웹 애플리케이션은 HTTP 기반
2) 웹 서버(Web Server)
3) 웹 애플리케이션 서버(WAS - Web Application Server)
4) 웹 서버 vs  웹 애플리케이션 서버(WAS)
5) 웹 시스템 구성 - WAS, DB
6) 웹 시스템 구성 - WEB, WAS, DB

### <a href="Chapter 01. 웹 애플리케이션의 이해/1.2 서블릿.md" target="_blank">1.2 서블릿</a>
1) 도입 배경 : WAS에서 처리해야하는 너무 많은 업무량
2) 서블릿의 도입
3) 서블릿을 통한 HTTP 요청, 응답의 흐름
4) 서블릿 컨테이너

### <a href="Chapter 01. 웹 애플리케이션의 이해/1.3 동시요청 - 멀티 스레드.md" target="_blank">1.3 동시요청 - 멀티 스레드</a>
1) 서블릿 호출의 주체는 스레드
2) 싱글 스레드의 한계 
3) 멀티 스레드 - 요청마다 스레드를 생성
4) 스레드 풀 : 요청마다 스레드 생성의 단점 보완
5) WAS의 주요 튜닝 포인트는 최대 스레드 수
6) WAS(서블릿 컨테이너 - 톰캣)의 멀티 스레드 관리 지원

### <a href="Chapter 01. 웹 애플리케이션의 이해/1.4 HTML, HTTP API, SSR, CSR.md" target="_blank">1.4 HTML, HTTP API, SSR, CSR</a>
1) 웹 컨텐츠 리소스
2) SSR : 서버 사이드 렌더링
3) CSR : 클라이언트 사이드 렌더링
4) 선택과 집중 - 어디까지 알아야할까?

### <a href="Chapter 01. 웹 애플리케이션의 이해/1.5 자바 백엔드 웹 기술 역사.md" target="_blank">1.5 자바 백엔드 웹 기술 역사</a>
1) 과거의 기술
2) 현재 활용 기술 - 어노테이션 기반 Spring MVC
3) 최신 기술 - Spring WebFlux?
4) 자바 뷰 템플릿 역사

---

## Chapter 02. 서블릿
### <a href="Chapter 02. 서블릿/2.01 프로젝트 생성.md" target="_blank">2.01 프로젝트 생성</a>
1) 프로젝트 생성
2) IDE 설정
3) Postman 설치 (API 호출)

### <a href="Chapter 02. 서블릿/2.02 Hello 서블릿.md" target="_blank">2.02 Hello 서블릿</a>
1) 기본적인 서블릿 환경 구성 방법
2) 스프링 부트에서 서블릿 자동 스캔 : `@ServletComponentScan`
3) 서블릿 등록하기 : `@WebServlet`, `extends HttpServlet`
4) 서블릿 실행하기
5) Http 요청 메시지 전체를 로깅하는 방법
6) 서블릿 컨테이너 동작 방식 설명
7) welcome 페이지 추가

### <a href="Chapter 02. 서블릿/2.03 HttpServletRequest - 개요.md" target="_blank">2.03 HttpServletRequest - 개요</a>
1) HttpServletRequest
2) Http 요청 메시지 파싱
3) 임시 저장소 기능
4) 세션 관리 기능
5) 결국 Http 스펙에 대한 이해가 중요

### <a href="Chapter 02. 서블릿/2.04 HttpServletRequest - 기본 사용법.md" target="_blank">2.04 HttpServletRequest - 기본 사용법</a>
1) 실습용 서블릿 생성 - `RequestHeaderServlet`
2) RequestLine 정보
3) 모든 요청 헤더, 요청 헤더 확인하기
4) 요청 헤더 관련 편의 메서드들
5) 기타 - 클라이언트측, 서버측 정보 조회 (remote, local)

### <a href="Chapter 02. 서블릿/2.05 Http 요청 데이터 - 개요.md" target="_blank">2.05 Http 요청 데이터 - 개요</a>
1) GET - 쿼리 파라미터
2) POST - HTML Form
3) HTTP message body에 데이터를 직접 담아서 요청

### <a href="Chapter 02. 서블릿/2.06 Http 요청 데이터 - GET 쿼리 파라미터.md" target="_blank">2.06 Http 요청 데이터 - GET 쿼리 파라미터</a>
작성 예정

### <a href="Chapter 02. 서블릿/2.07 Http 요청 데이터 - POST HTML Form.md" target="_blank">2.07 Http 요청 데이터 - POST HTML Form</a>
작성 예정

### <a href="Chapter 02. 서블릿/2.08 Http 요청 데이터 - API 메시지 바디 - 단순 텍스트.md" target="_blank">2.08 Http 요청 데이터 - API 메시지 바디 - 단순 텍스트</a>
작성 예정

### <a href="Chapter 02. 서블릿/2.09 Http 요청 데이터 - API 메시지 바디 - JSON.md" target="_blank">2.09 Http 요청 데이터 - API 메시지 바디 - JSON</a>
작성 예정

### <a href="Chapter 02. 서블릿/2.10 HttpServletResponse - 기본 사용법.md" target="_blank">2.10 HttpServletResponse - 기본 사용법</a>
작성 예정

### <a href="Chapter 02. 서블릿/2.11 Http 응답 데이터 - 단순 텍스트, HTML.md" target="_blank">2.11 Http 응답 데이터 - 단순 텍스트, HTML</a>
작성 예정

### <a href="Chapter 02. 서블릿/2.12 Http 응답 데이터 - API JSON.md" target="_blank">2.12 Http 응답 데이터 - API JSON</a>
작성 예정

---

## Chapter 03. 서블릿, JSP, MVC 패턴
- 3.01 회원 관리 웹 애플리케이션 요구사항
- 3.02 서블릿으로 회원 관리 웹 애플리케이션 만들기
- 3.03 JSP로 회원 관리 웹 애플리케이션 만들기
- 3.04 MVC 패턴 - 개요
- 3.05 MVC 패턴 - 적용
- 3.06 MVC 패턴 - 한계

---

## Chapter 04. MVC 프레임워크 만들기
- 4.01 프론트 컨트롤러 패턴 소개
- 4.02 프론트 컨트롤러 도입 - v1
- 4.03 View 분리 - v2
- 4.04 Model 추가 - v3
- 4.05 단순하고 실용적인 컨트롤러 - v4
- 4.06 유연한 컨트롤러1 - v5
- 4.07 유연한 컨트롤러2 - v5

---

## Chapter 05. 스프링 MVC - 구조 이해
- 5.01 스프링 MVC 전체 구조
- 5.02 핸들러 매핑과 핸들러 어댑터
- 5.03 뷰 리졸버
- 5.04 스프링 MVC - 시작하기
- 5.05 스프링 MVC - 컨트롤러 통합
- 5.06 스프링 MVC - 실용적인 방식

---

## Chapter 06. 스프링 MVC - 기본 기능
- 6.01 프로젝트 생성
- 6.02 요구사항 분석
- 6.03 상품 도메인 개발
- 6.04 상품 서비스 HTML
- 6.05 상품 목록 - 타임리프
- 6.06 상품 상세
- 6.07 상품 등록 폼
- 6.08 상품 등록 처리 - @ModelAttribute
- 6.09 상품 수정
- 6.10 PRG Post/Redirect/Get
- 6.11 RedirectAttributes

---
