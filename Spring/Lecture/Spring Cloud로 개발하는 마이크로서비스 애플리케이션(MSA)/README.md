
# Spring Cloud로 개발하는 마이크로서비스 애플리케이션(MSA)

---

## Chapter 01. Microservice와 Spring Cloud의 소개

### <a href="Chapter 01. Microservice와 Spring Cloud의 소개/1.1 소프트웨어 아키텍처.md">1.1 소프트웨어 아키텍처</a>
1) IT 시스템의 발전 역사
2) Anti-Fragile의 특징1 : Auto Scaling
3) Anti-Fragile의 특징2 : Microservices
4) Anti-Fragile의 특징3 : Chaos Engineering
5) Anti-Fragile의 특징3 : Chaos Engineering

### <a href="Chapter 01. Microservice와 Spring Cloud의 소개/1.2 Cloud Native Architecture의 특징.md">1.2 Cloud Native Architecture의 특징</a>
1) 확장 가능한 아키텍처
2) 탄력적인 아키텍처
3) 장애 격리(Fault isolation)

### <a href="Chapter 01. Microservice와 Spring Cloud의 소개/1.3 Cloud Native Application.md">1.3 Cloud Native Application</a>
1) Microservices
2) CI/CD
3) DevOps
4) Container 가상화

### <a href="Chapter 01. Microservice와 Spring Cloud의 소개/1.4 12 + 3 Factors.md">1.4 12 + 3 Factors</a>

클라우드 애플리케이션을 구축함에 있어 고려해봐야할 12 + 3가지 항목들
1) Codebase : 코드베이스
2) Dependencies : 명시적인 종속성 선언 및 격리
3) Config : 환경설정의 외부 관리
4) Backing services : 보조 서비스를 연결된 리소스로 취급한다
5) Build, release, run : 빌드, 릴리즈, 실행 단계를 엄격히 분리하라
6) Stateless Processes : 무상태 프로세스
7) Port binding : 포트 바인딩을 통한 프로세스 격리, 구별
8) Concurrency : 프로세스 모델(Process Model)을 통한 수평 확장
9) Disposability : 빠른 시작/종료, graceful shutdown을 통한 안정성 극대화
10) Dev/prod parity : 서비스의 개발/스테이징/운영 환경을 최대한 비슷하게 유지
11) Logs : 로그를 이벤트 스트림으로 처리하고, 실행환경에서 수집하여 외부에 병합
12) Admin processes : 어드민, 메인터넌스 작업을 일회성 프로세스로 실행
13) API First : API의 명확한 설계가 중요하다.
14) Telemetry : 원격 분석
15) Authentication and authorization : 인증과 인가

### <a href="Chapter 01. Microservice와 Spring Cloud의 소개/1.5 Monolithic vs. Microservice.md">1.5 Monolithic vs. Microservice</a>
1) Monolithic Architecture
2) Microservice Architecture

### <a href="Chapter 01. Microservice와 Spring Cloud의 소개/1.6 Microservice Architecture.md">1.6 Microservice Architecture</a>
1) 마이크로서비스가 가져야할 특징들
2) 반드시 마이크로서비스 아키텍처를 사용해야 하는가? : 아니오아니오

### <a href="Chapter 01. Microservice와 Spring Cloud의 소개/1.7 SOA vs. MSA.md">1.7 SOA vs. MSA</a>
1) SOA(Service Oriented Architecture)
2) MSA (MicroService Architecture)
3) REST 제약조건
4) REST API 설계 시 고려할 사항

### <a href="Chapter 01. Microservice와 Spring Cloud의 소개/1.8 Microservice Architecture Structures.md">1.8 Microservice Architecture Structures</a>
1) 주요 제품들

### <a href="Chapter 01. Microservice와 Spring Cloud의 소개/1.9 Spring Cloud.md">1.9 Spring Cloud</a>
1) 스프링 클라우드란?
2) 사용
3) 필수 SW

---

## Chapter 02. Service Discovery

### <a href="Chapter 02. Service Discovery/2.1 Service Discovery.md">2.1 Service Discovery</a>
1) Service Discovery란?

### <a href="Chapter 02. Service Discovery/2.2 Eureka Service Discovery - 프로젝트 생성.md">2.2 Eureka Service Discovery - 프로젝트 생성</a>
1) 프로젝트 생성
2) application.yml
3) `@EnableEurekaServer` : 유레카 서비스 활성화
4) 실행

---

## Chapter 03. API Gateway Service

---

## Chapter 04. E-commerce 애플리케이션

---

## Chapter 05. Users Microservice

---

## Chapter 06. Catalogs and Orders Microservice

---

## Chapter 07. Users Microservice 

---

## Chapter 08. Configuration Service

---

## Chapter 09. Spring Cloud Bus

---

## Chapter 10. 설정 정보의 암호화 처리

---

## Chapter 11. Microservice간 통신

---

## Chapter 12. 데이터 동기화를 위한 Apache Kafka의 활용 1

---

## Chapter 13. 데이터 동기화를 위한 Apache Kafka의 활용 

---

## Chapter 14. 장애 처리와 Microservice 분산 추적

---

## Chapter 15. Microservice 모니터링

---

## Chapter 16. 애플리케이션 배포를 위한 컨테이너 가상화

---

## Chapter 17. 애플리케이션 배포 - Docker Container

---

## Chapter 18. Appendix: Microservice Architecture 패턴

---
