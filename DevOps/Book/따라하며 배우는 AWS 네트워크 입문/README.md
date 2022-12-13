
# 따라하며 배우는 AWS 네트워크 입문

---

# Chapter 01. AWS 인프라

## 다루는 내용
- 클라우드에 대한 기본 개념
- AWS 인프라, 서비스
- 실제 EC2 인스턴스 배포 실습
- CloudFormation 을 통한 인프라 자동 배포

### <a href="Chapter 01. AWS 인프라/1.1 AWS 소개.md" target="_blank">1.1 AWS 소개</a>
1) 클라우드
2) AWS 클라우드
3) AWS 제품

### <a href="Chapter 01. AWS 인프라/1.2 AWS Network 소개.md" target="_blank">1.2 AWS Network 소개</a>
- AWS VPC : 리소스 격리. 가상 클라우드 네트워크
  - 사용자가 정의한 가상 네트워크 상에서 다양한 AWS 리소스를 실행할 수 있게 지원
- AWS VPN : 가상 사설망
  - 프라이빗 통신 제공 -> 데이터 암호화, 전용 연결 등 보안 요구사항 충족
  - Site-to-Site VPN, 클라이언트 VPN
- ELB : 로드 밸런싱
  - 서비스 대상 시스템(예: EC2)에 데이터 분산
- AWS Private Link : 프라이빗 연결
  - 퍼블릭 인터넷에 데이터가 노출되지 않도록 하고, 내부 네트워크를 통해 AWS 서비스-온프레미스 간 안전한 비공개 연결 제공
- Route 53 : 도메인 네임 시스템
  - AWS에서 제공하는 관리형 DNS 서비스
  - 도메인 이름 구해 대행, 구매 도메인 주소에 대한 호스팅 영역 설정을 통하여 도메인 질의에 대한 응답 처리
  - 그 외에도 Route 53 Resolver 기능 -> 하이브리드 클라우드 환경에서의 온프레미스-AWS 간 도메인 질의를 가능하게 함
- AWS 전송 게이트웨이 : 네트워크 확장
  - VPC, 온프레미스 등 네트워크를 단일 지점으로 연결할 수 있는 라우팅 서비스
- AWS Direct Connect : AWS 전용 연결
  - 데이터 센터, 본사 사무실 또는 코로케이션 환경과 같은 장소에서 AWS와의 전용 네트워크 연결 제공(전용선 서비스)
- AWS CloudFront : CDN(콘텐츠 전송, 캐시)
  - AWS에서 제공하는 CDN(Contents Deleviery Network) 서비스
  - AWS 글로벌 네트워크를 통해 전세계 316개의 엣지 POP으로, 콘텐츠를 캐싱하여 서비스를 제공
- AWS Global Accelerator : 글로벌 전송
  - 로컬 또는 글로벌 사용자를 대상으로 애플리케이션의 가용성, 성능 개선
  - AWS 글로벌 네트워크를 통해 사용자에서 애플리케이션으로 이어진 경로를 최적화하여 트래픽 성능 개선
- 네트워크 보안
  - AWS 네트워크 기반의 보안 기능
  - 보안 그룹, 네트워크 ACL, 웹 방화벽 등...

### <a href="Chapter 01. AWS 인프라/1.3 실습 전 사전 준비 사항.md" target="_blank">1.3 실습 전 사전 준비 사항</a>
작성 예정

### <a href="Chapter 01. AWS 인프라/1.4 EC2 배포 및 사용.md" target="_blank">1.4 EC2 배포 및 사용</a>
작성 예정

### <a href="Chapter 01. AWS 인프라/1.5 CloudFormation 스택 생성 및 삭제.md" target="_blank">1.5 CloudFormation 스택 생성 및 삭제</a>
작성 예정

---

# Chapter 02. VPC 기초

### <a href="Chapter 02. VPC 기초/2.1 VPC(Virtual Private Cloud).md" target="_blank">2.1 VPC(Virtual Private Cloud)</a>
작성 예정

### <a href="Chapter 02. VPC 기초/2.2 기본 네트워크 개념 이해.md" target="_blank">2.2 기본 네트워크 개념 이해</a>
작성 예정

### <a href="Chapter 02. VPC 기초/2.3 VPC 리소스 소개.md" target="_blank">2.3 VPC 리소스 소개</a>
작성 예정

### <a href="Chapter 02. VPC 기초/2.4 [실습 2-1] 퍼블릭 서브넷 VPC 구성.md" target="_blank">2.4 [실습 2-1] 퍼블릭 서브넷 VPC 구성</a>
작성 예정

### <a href="Chapter 02. VPC 기초/2.5 [실습 2-2] 프라이빗 서브넷 VPC 구성.md" target="_blank">2.5 [실습 2-2] 프라이빗 서브넷 VPC 구성</a>
작성 예정

---

# Chapter 03. VPC 고급

---

# Chapter 04. 인터넷 연결

---

# Chapter 05. 부하 분산

---

# Chapter 06. 네트워크 연결 옵션

---

# Chapter 07. 네트워크 보안

---

# Chapter 08. 종합 실습

---
