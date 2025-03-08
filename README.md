### tstudy

---

#### Back-end
- <a href="./back-end/동시성 문제.md" target="_blank">동시성 문제</a>
- <a href="./back-end/메시지 큐, 이벤트 스트림.md" target="_blank">메시지 큐, 이벤트 스트림</a>
- 부하테스트
  - 부하테스트 기본 개념
    - <a href="./back-end/부하 테스트란, 부하테스트를 하는 이유.md" target="_blank">부하 테스트란, 부하테스트를 하는 이유</a>
    - <a href="./back-end/처리량(Throughput), 지연 시간(Latency).md" target="_blank">처리량(Throughput), 지연 시간(Latency)</a>
    - <a href="./back-end/부하 테스트 툴.md" target="_blank">부하 테스트 툴</a>
    - <a href="./back-end/(실습) EC2에 간단한 테스트용 API 서버 셋팅하기.md" target="_blank">(실습) EC2에 간단한 테스트용 API 서버 셋팅하기</a>
    - <a href="./back-end/(실습) EC2에 부하 테스트 툴 셋팅하기(k6).md" target="_blank">(실습) EC2에 부하 테스트 툴 셋팅하기(k6)</a>
    - <a href="./back-end/(실습) 내가 구성한 백엔드 서버는 1초당 몇 개의 요청을 견뎌낼 수 있을까.md" target="_blank">(실습) 내가 구성한 백엔드 서버는 1초당 몇 개의 요청을 견뎌낼 수 있을까</a>
  - 부하테스트를 통한 병목 지점 진단
    - <a href="./back-end/병목 지점(Bottleneck Point).md" target="_blank">병목 지점 (Bottleneck Point)</a>
    - <a href="./back-end/부하 테스트의 전체 흐름.md" target="_blank">부하 테스트의 전체 흐름</a>
    - <a href="./back-end/부하 테스트 시 주의점.md" target="_blank">부하 테스트 시 주의점</a>
    - <a href="./back-end/(실습) 부하 테스트 할 인프라 구성을 그림으로 파악하기.md" target="_blank">(실습) 부하 테스트 할 인프라 구성을 그림으로 파악하기</a>
    - 모니터링, 메트릭
    - CPU, 메모리, 디스크
    - EC2 모니터링 셋팅
    - RDS 모니터링 셋팅
    - ELB의 CPU, 메모리를 측정하지 않는 이유
    - 각 서버의 CPU, 메모리를 한 눈에 볼 수 있도록 셋팅하기
    - 부하테스트를 통해 병목 지점 진단하기
    - 실시간으로 CPU 와 메모리를 관측하는 방법
  - 병목 지점 해결을 통한 성능 개선
    - 가용성, 시스템 이중화
    - 수평적 확장, 수직적 확장, 캐싱
    - 트래픽 증가에 따른 시스템 설계 및 확장 방법
    - 병목지점(DB) 해결
    - 병목지점(웹 애플리케이션 서버) 해결하기
    - 부하테스트 전체 흐름 다시 점검

---

#### DevOps
- 도커(Docker)
  - <a href="./devops/docker/Windows 에서 Docker 설치.md" target="_blank">Windows 에서 Docker 설치</a>
  - <a href="./devops/docker/도커 컴포즈(Docker Compose).md" target="_blank">도커 컴포즈(Docker Compose)</a>
- <a href="./devops/kubernetes/쿠버네티스(Kubernetes).md" target="_blank">쿠버네티스(Kubernetes)</a>
  - <a href="./devops/kubernetes/남들보다 훨씬 쿠버네티스를 빠르게 배우는 방법.md" target="_blank">남들보다 훨씬 쿠버네티스를 빠르게 배우는 방법</a>
  - <a href="./devops/kubernetes/Windows 에서 쿠버네티스 설치.md" target="_blank">Windows 에서 쿠버네티스 설치</a>
  - <a href="./devops/kubernetes/GKE 쿠버네티스 클러스터 생성.md" target="_blank">GKE 쿠버네티스 클러스터 생성</a>
  - <a href="./devops/kubernetes/GKE 클러스터 사용 및 애플리케이션 배포.md" target="_blank">GKE 클러스터 사용 및 애플리케이션 배포</a>
  - <a href="./devops/kubernetes/GCE VM 을 통한 클러스터 구성, 애플리케이션 배포.md" target="_blank">GCE VM 을 통한 클러스터 구성, 애플리케이션 배포</a>
  - <a href="./devops/kubernetes/쿠버네티스 핵심 개념 - 파드(Pod), 디플로이먼트(Deployment), 서비스(Service).md" target="_blank">쿠버네티스 핵심 개념 - 파드(Pod), 디플로이먼트(Deployment), 서비스(Service)</a>
  - <a href="./devops/kubernetes/쿠버네티스 명령어 정리.md" target="_blank">쿠버네티스 명령어 정리</a>
  - <a href="./devops/kubernetes/파드(Pod).md" target="_blank">파드(Pod)</a>
  - <a href="./devops/kubernetes/파드 생성.md" target="_blank">파드 생성</a>
  - <a href="./devops/kubernetes/파드 외부에서 파드 내부 프로그램에 접근하기(포트 포워딩).md" target="_blank">파드 외부에서 파드 내부 프로그램에 접근하기(포트 포워딩)</a>
  - <a href="./devops/kubernetes/(예제) 백엔드(Spring Boot) 서버를 파드(Pod)로 띄워보기.md" target="_blank">(예제) 백엔드(Spring Boot) 서버를 파드(Pod)로 띄워보기</a>
  - <a href="./devops/kubernetes/이미지가 없다고 에러가 뜨는 이유 (이미지 풀 정책).md" target="_blank">이미지가 없다고 에러가 뜨는 이유 (이미지 풀 정책)</a>
  - <a href="./devops/kubernetes/(예제) 백엔드(Nest.js) 서버를 파드(Pod)로 띄워보기.md" target="_blank">(예제) 백엔드(Nest.js) 서버를 파드(Pod)로 띄워보기</a>
  - <a href="./devops/kubernetes/(예제) 프론트엔드(HTML,CSS,Nginx) 서버를 파드(Pod)로 띄워보기.md" target="_blank">(예제) 프론트엔드(HTML,CSS,Nginx) 서버를 파드(Pod)로 띄워보기</a>
  - <a href="./devops/kubernetes/(예제) 프론트엔드(Next.js) 서버를 파드(Pod)로 띄워보기.md" target="_blank">(예제) 프론트엔드(Next.js) 서버를 파드(Pod)로 띄워보기</a>
  - <a href="./devops/kubernetes/파드(Pod) 디버깅하는 방법.md" target="_blank">파드(Pod) 디버깅하는 방법</a>
  - <a href="./devops/kubernetes/백엔드(Spring Boot) 서버 3개 띄워보기.md" target="_blank">백엔드(Spring Boot) 서버 3개 띄워보기</a>
  - <a href="./devops/kubernetes/디플로이먼트(Deployment).md" target="_blank">디플로이먼트(Deployment)</a>
  - <a href="./devops/kubernetes/(예제) 디플로이먼트를 활용해 백엔드(Spring Boot) 서버 3개 띄워보기.md" target="_blank">(예제) 디플로이먼트를 활용해 백엔드(Spring Boot) 서버 3개 띄워보기</a>
  - <a href="./devops/kubernetes/서비스(Service).md" target="_blank">서비스(Service)</a>
  - <a href="./devops/kubernetes/(예제) 서비스(Service)를 활용해 백엔드(Spring Boot) 서버와 통신해보기.md" target="_blank">(예제) 서비스(Service)를 활용해 백엔드(Spring Boot) 서버와 통신해보기</a>
  - <a href="./devops/kubernetes/디플로이먼트를 활용한 서버 개수 조절 방법.md" target="_blank">디플로이먼트를 활용한 서버 개수 조절 방법</a>
  - <a href="./devops/kubernetes/서버가 죽었을 때 자동으로 복구하는 기능 (Self-Healing).md" target="_blank">서버가 죽었을 때 자동으로 복구하는 기능 (Self-Healing)</a>
  - <a href="./devops/kubernetes/새로운 버전의 서버로 업데이트 시키기.md" target="_blank">새로운 버전의 서버로 업데이트 시키기</a>
  - <a href="./devops/kubernetes/(예제) 디플로이먼트, 서비스를 활용해 백엔드(Nest.js) 서버 띄워보기.md" target="_blank">(예제) 디플로이먼트, 서비스를 활용해 백엔드(Nest.js) 서버 띄워보기</a>
  - <a href="./devops/kubernetes/(예제) 백엔드(Spring Boot) 서버에 환경변수 등록해 사용하기.md" target="_blank">(예제) 백엔드(Spring Boot) 서버에 환경변수 등록해 사용하기</a>
  - <a href="./devops/kubernetes/컨피그맵(ConfigMap)을 활용해 환경변수 분리하기.md" target="_blank">컨피그맵(ConfigMap)을 활용해 환경변수 분리하기</a>
  - <a href="./devops/kubernetes/시크릿(Secret)을 활용해 '민감한 값'을 환경 변수로 분리하기.md" target="_blank">시크릿(Secret)을 활용해 '민감한 값'을 환경 변수로 분리하기</a>
  - <a href="./devops/kubernetes/볼륨(Volume).md" target="_blank">볼륨(Volume)</a>
  - <a href="./devops/kubernetes/(예제) 디플로이먼트(Deployment)를 활용해 MySQL 실행시키기.md" target="_blank">(예제) 디플로이먼트(Deployment)를 활용해 MySQL 실행시키기</a>
  - <a href="./devops/kubernetes/볼륨(Volume)을 활용해 MySQL 실행시키기.md" target="_blank">볼륨(Volume)을 활용해 MySQL 실행시키기</a>
  - <a href="./devops/kubernetes/(예제) 백엔드(Spring Boot) 서버와 MySQL 연동하기.md" target="_blank">(예제) 백엔드(Spring Boot) 서버와 MySQL 연동하기</a>
  - <a href="./devops/kubernetes/스프링 서버와 MySQL이 제대로 연결되지 않을 때.md" target="_blank">스프링 서버와 MySQL이 제대로 연결되지 않을 때</a>
  - <a href="./devops/kubernetes/보안을 위해 외부에서 MySQL 접근하지 못하도록 막기.md" target="_blank">보안을 위해 외부에서 MySQL 접근하지 못하도록 막기</a>
  - <a href="./devops/kubernetes/k3s.md" target="_blank">k3s</a>
  - <a href="./devops/kubernetes/EC2에서 도커,쿠버네티스 설치하기 (k3s).md" target="_blank">EC2에서 도커,쿠버네티스 설치하기 (k3s)</a>
  - <a href="./devops/kubernetes/(예제) 디플로이먼트, 서비스를 활용해 EC2에 웹 서버(Nginx) 띄워보기.md" target="_blank">(예제) 디플로이먼트, 서비스를 활용해 EC2에 웹 서버(Nginx) 띄워보기</a>
  - <a href="./devops/kubernetes/(예제) 백엔드(Spring Boot) 서버 EC2에 배포하기, DB 연동하기 (+RDS,ECR).md" target="_blank">(예제) 백엔드(Spring Boot) 서버 EC2에 배포하기, DB 연동하기 (+RDS,ECR)</a>
  - <a href="./devops/kubernetes/RDS, ECR 생성하기.md" target="_blank">RDS, ECR 생성하기</a>
  - <a href="./devops/kubernetes/EC2에 배포할 백엔드(Spring Boot) 서버 프로젝트, 매니페스트 파일 구성하기.md" target="_blank">EC2에 배포할 백엔드(Spring Boot) 서버 프로젝트, 매니페스트 파일 구성하기</a>
  - <a href="./devops/kubernetes/백엔드(Spring Boot) 서버 빌드한 후 ECR로 Push하기.md" target="_blank">백엔드(Spring Boot) 서버 빌드한 후 ECR로 Push하기</a>
  - <a href="./devops/kubernetes/EC2가 ECR로부터 이미지를 Pull 받아올 수 있게 권한 부여하기.md" target="_blank">EC2가 ECR로부터 이미지를 Pull 받아올 수 있게 권한 부여하기</a>
  - <a href="./devops/kubernetes/EC2에서 쿠버네티스로 백엔드(Spring Boot) 서버 띄우기.md" target="_blank">EC2에서 쿠버네티스로 백엔드(Spring Boot) 서버 띄우기</a>
  - <a href="./devops/kubernetes/EC2에 배포된 백엔드(Spring Boot) 서버 업데이트하기.md" target="_blank">EC2에 배포된 백엔드(Spring Boot) 서버 업데이트하기</a>
  - <a href="./devops/kubernetes/EKS(Elastic Kubernetes Service).md" target="_blank">EKS(Elastic Kubernetes Service)</a>
  - <a href="./devops/kubernetes/쿠버네티스와 EKS의 아키텍처 구조.md" target="_blank">쿠버네티스와 EKS의 아키텍처 구조</a>
  - <a href="./devops/kubernetes/EKS 클러스터 생성하기.md" target="_blank">EKS 클러스터 생성하기</a>
  - <a href="./devops/kubernetes/EKS 워커 노드 추가하기.md" target="_blank">EKS 워커 노드 추가하기</a>
  - <a href="./devops/kubernetes/로컬에서 EKS 클러스터 조정할 수 있게 셋팅하기.md" target="_blank">로컬에서 EKS 클러스터 조정할 수 있게 셋팅하기</a>
  - <a href="./devops/kubernetes/EKS에 백엔드(Spring Boot) 서버 배포하기 (+RDS,ECR).md" target="_blank">EKS에 백엔드(Spring Boot) 서버 배포하기 (+RDS,ECR)</a>
  - <a href="./devops/kubernetes/비용 나가지 않게 EKS 종료하기.md" target="_blank">비용 나가지 않게 EKS 종료하기</a>
- AWS
  - <a href="./devops/aws/AWS CLI 설치.md" target="_blank">AWS CLI 설치</a>

---

#### Java
- <a href="./java/ThreadLocal.md">ThreadLocal</a>

---

#### Spring
- <a href="./spring/로케일 - LocaleContext, LocaleResolver.md">로케일 - LocaleContext, LocaleResolver</a>
- <a href="./spring/spring-data-jpa/p6spy.md">p6spy</a>
- <a href="./spring/querydsl/Querydsl.md">QueryDsl</a>
  - <a href="./spring/querydsl/Querydsl 설정.md">QueryDsl 설정</a>
  - <a href="./spring/querydsl/Querydsl 예제 도메인 모델.md">Querydsl 예제 도메인 모델</a>
  - <a href="./spring/querydsl/JPQL vs Querydsl.md">JPQL vs Querydsl</a>
- <a href="./spring/스프링 시큐리티에 코틀린 DSL 적용하기.md" target="_blank">스프링 시큐리티에 코틀린 DSL 적용하기</a>
- <a href="./spring/스프링의 OAuth2 관련 프로젝트들.md" target="_blank">스프링의 OAuth2 관련 프로젝트들</a>
- <a href="./spring/Spring Security OAuth2 Client - application.yml 설정 및 OAuth2ClientProperties.md" target="_blank">Spring Security OAuth2 Client - application.yml 설정 및 OAuth2ClientProperties</a>
- <a href="./spring/Spring Security OAuth2 Client - ClientRegistration, ClientRegistrationRepository.md" target="_blank">Spring Security OAuth2 Client - ClientRegistration, ClientRegistrationRepository</a>
- <a href="./spring/Spring Security OAuth2 Client - OAuth2LoginConfigurer 초기화 이해.md" target="_blank">Spring Security OAuth2 Client - OAuth2LoginConfigurer 초기화 이해</a>
- <a href="./spring/Spring Security OAuth2 Client - 자동구성.md" target="_blank">Spring Security OAuth2 Client - 자동구성</a>

---

#### DataBase
- <a href="./database/기본키(PK, Primary Key) 생성 전략.md" target="_blank">기본키(PK, Primary Key) 생성 전략</a>
- <a href="./database/데이터베이스 모델링이란.md" target="_blank">데이터베이스 모델링이란</a>
  - <a href="./database/데이터베이스 설계 규칙 (1) 한 칸에는 한 가지 정보만 들어가도록 만들어라.md" target="_blank">데이터베이스 설계 규칙 (1) 한 칸에는 한 가지 정보만 들어가도록 만들어라</a>
  - <a href="./database/데이터베이스 설계 규칙 (2) 어떤 테이블에 FK를 넣어도 '규칙 1'을 못 지킬 때는 중간 테이블을 하나 더 만들어라.md" target="_blank">데이터베이스 설계 규칙 (2) 어떤 테이블에 FK를 넣어도 '규칙 1'을 못 지킬 때는 중간 테이블을 하나 더 만들어라</a>
  - <a href="./database/데이터베이스 설계 규칙 (3) 헷갈릴 땐 관계(1：1, 1：N, M：N)를 파악해봐라.md" target="_blank">데이터베이스 설계 규칙 (3) 헷갈릴 땐 관계(1：1, 1：N, M：N)를 파악해봐라</a>
  - <a href="./database/데이터베이스 설계 규칙 (4) 데이터 중복이 발생하는 컬럼이 있는 지 확인해라.md" target="_blank">데이터베이스 설계 규칙 (4) 데이터 중복이 발생하는 컬럼이 있는 지 확인해라</a>
  - <a href="./database/데이터베이스 설계 규칙 (5) 가짜 중복과 진짜 중복을 구별해라.md" target="_blank">데이터베이스 설계 규칙 (5) 가짜 중복과 진짜 중복을 구별해라</a>
  - <a href="./database/데이터베이스 설계 규칙 (6) 숨어있는 중복을 찾아라(집계값).md" target="_blank">데이터베이스 설계 규칙 (6) 숨어있는 중복을 찾아라(집계값)</a>
- <a href="./database/데이터베이스 성능 최적화.md" target="_blank">데이터베이스 성능 최적화</a>
  - <a href="./database/데이터베이스 아키텍처와 SQL 튜닝.md" target="_blank">데이터베이스 아키텍처와 SQL 튜닝</a>
  - <a href="./database/인덱스.md" target="_blank">인덱스</a>
  - <a href="./database/기본으로 설정되는 인덱스(PK).md" target="_blank">기본으로 설정되는 인덱스(PK)</a>
  - <a href="./database/제약조건을 추가하면 자동으로 추가되는 인덱스(UNIQUE).md" target="_blank">제약조건을 추가하면 자동으로 추가되는 인덱스(UNIQUE)</a>
  - <a href="./database/인덱스를 과도하게 많이 추가하지 마라.md" target="_blank">인덱스를 과도하게 많이 추가하지 마라</a>
  - <a href="./database/멀티 칼럼 인덱스(Multi-column Index).md" target="_blank">멀티 칼럼 인덱스(Multi-column Index)</a>
  - <a href="./database/멀티 칼럼 인덱스 생성 시 주의점.md" target="_blank">멀티 칼럼 인덱스 생성 시 주의점</a>
  - <a href="./database/커버링 인덱스(Covering Index).md" target="_blank">커버링 인덱스(Covering Index)</a>
  - <a href="./database/실행 계획(Execution plan).md" target="_blank">실행 계획(Execution plan)</a>
  - <a href="./database/실행 계획에서 type의 의미.md" target="_blank">실행 계획에서 type의 의미</a>
  - <a href="./database/목록 조회시 너무 많이 조회하지 않도록 데이터의 건수를 지정하자(LIMIT).md" target="_blank">목록 조회시 너무 많이 조회하지 않도록 데이터의 건수를 지정하자(LIMIT)</a>
- MySQL
  - <a href="./database/mysql/MySQL - Docker를 통한 MySQL 환경 구성.md" target="_blank">MySQL - Docker를 통한 MySQL 환경 구성</a>
  - <a href="./database/mysql/언두 로그와 MVCC (Multi Version Concurrency Control).md" target="_blank">언두 로그와 MVCC (Multi Version Concurrency Control)</a>
  - <a href="./database/mysql/MySQL 데이터 타입.md" target="_blank">MySQL 데이터 타입</a>
  - <a href="./database/mysql/CTE(Common Table Expression) - WITH 와 WITH RECURSIVE.md" target="_blank">CTE(Common Table Expression) - WITH 와 WITH RECURSIVE</a>
- <a href="./database/redis/레디스(Redis).md" target="_blank">레디스(Redis)</a>
  - <a href="./database/redis/Redis - Docker를 통한 Redis 환경 구성.md" target="_blank">Redis - Docker를 통한 Redis 환경 구성</a>
  - <a href="./database/redis/레디스 기본 명령어.md" target="_blank">레디스 기본 명령어</a>
  - <a href="./database/redis/레디스 Key 네이밍 컨벤션.md" target="_blank">레디스 Key 네이밍 컨벤션</a>
  - <a href="./database/redis/캐시(Cache), 캐싱(Caching)이란.md" target="_blank">캐시(Cache), 캐싱(Caching)이란</a>

---

#### MSA
- <a href="./msa/서비스 디스커버리(Service Discovery).md" target="_blank">서비스 디스커버리(Service Discovery)</a>
- <a href="./msa/서비스 디스커버리 - Spring Eureka Server 실습.md" target="_blank">서비스 디스커버리 - Spring Eureka Server 실습</a>

---

#### Kafka
- <a href="./kafka/Kafka - Docker를 통한 Kafka 환경 구성.md" target="_blank">Kafka - Docker를 통한 Kafka 환경 구성</a>
- <a href="./kafka/Kafka - 토픽 생성, 조회, 삭제.md" target="_blank">Kafka - 토픽 생성, 조회, 삭제</a>

---

#### HTML
- <a href="./html/id와 class.md" target="_blank">id와 class</a>

---

#### CSS
- <a href="./css/HTML-CSS 연결.md" target="_blank">HTML-CSS 연결</a>
- <a href="./css/색상.md" target="_blank">색상</a>
- <a href="./css/단위.md" target="_blank">단위</a>

---

#### JavaScript
- <a href="./javascript/Node.js 설치.md" target="_blank">Node.js 설치</a>

---

#### React
- <a href="./react/useState.md" target="_blank">useState - 상태 관리</a>
- <a href="./react/TanStack Query 설치.md" target="_blank">TanStack Query 설치</a>

---

#### Next.js
- <a href="./nextjs/Next.js 프로젝트 생성.md" target="_blank">Next.js 프로젝트 생성</a>

---

#### Python
- <a href="./python/Python 로컬 개발환경 구성.md" target="_blank">Python 로컬 개발환경 구성</a>
- <a href="./python/문자열.md" target="_blank">문자열</a>

---

#### DataStructure & Algorithm
- <a href="./data-structure-and-algorithm/시간복잡도, 공간복잡도.md" href="_blank">시간복잡도, 공간복잡도</a>
- <a href="./data-structure-and-algorithm/배열.md" href="_blank">배열</a>
- <a href="./data-structure-and-algorithm/재귀함수.md" href="_blank">재귀함수</a>
- <a href="./data-structure-and-algorithm/연결 리스트(Linked List).md" href="_blank">연결 리스트(Linked List)</a>
- <a href="./data-structure-and-algorithm/이진 탐색(Binary Search).md" href="_blank">이진 탐색(Binary Search)</a>
- <a href="./data-structure-and-algorithm/정렬.md" href="_blank">정렬</a>
- <a href="./data-structure-and-algorithm/스택.md" href="_blank">스택</a>
- <a href="./data-structure-and-algorithm/큐(Queue).md" href="_blank">큐(Queue)</a>
- <a href="./data-structure-and-algorithm/해쉬.md" href="_blank">해쉬</a>
- <a href="./data-structure-and-algorithm/트리(Tree).md" href="_blank">트리(Tree)</a>
- <a href="./data-structure-and-algorithm/힙(Heap).md" href="_blank">힙(Heap)</a>
- <a href="./data-structure-and-algorithm/그래프(Graph).md" href="_blank">그래프(Graph)</a>
- <a href="./data-structure-and-algorithm/DFS & BFS.md" href="_blank">DFS & BFS</a>
- <a href="./data-structure-and-algorithm/DP(Dynamic Programming).md" href="_blank">DP(Dynamic Programming)</a>

---
