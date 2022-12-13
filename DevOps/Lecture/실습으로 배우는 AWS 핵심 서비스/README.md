# 실습으로 배우는 AWS 핵심 서비스

- 호눅스 강의 : https://www.inflearn.com/course/aws-%ED%95%B5%EC%8B%AC-%EC%8B%A4%EC%8A%B5

---

## Intro : 강의 소개
- AWS 시작하기
- AWS 관리 콘솔과 루트 계정

---

## Chapter 01. AWS Global Infrastructure
### 1.1 AWS Global Infrastructure

---

## Chapter 02. IAM 실습

### <a href="Chapter 02. IAM 실습/2.1 ROOT 사용자 MFA 적용하기.md" target="_blank">2.1 ROOT 사용자 MFA 적용하기</a>
1) 필요성 : 루트 사용자는 보안 상 매우 중요한 계정
2) 적용 방법
3) 주의점 : 휴대폰 교체 시 MFA 비활성화

### <a href="Chapter 02. IAM 실습/2.2 admin 사용자 추가.md" target="_blank">2.2 admin 사용자 추가</a>
1) admin 그룹 생성 및 사용자 연결

### 2.3 개발자 아이디 추가
### 2.4 로그인 URL 변경하기

---

## Chapter 03. IAM Policy
### 3.1 인증과 권한 부여
### 3.2 IAM Policy
### 3.3 IAM Policy 예제

---

## Chapter 04. IAM Role
### 4.1 IAM Role
### 4.2 IAM Role의 구성요소
### 4.3 IAM Role 사용예

---

## Chapter 05. IAM Role 실습
### 5.1 Switch Role 만들기
### 5.2 Switch Role 사용하기
### 5.3 CLI 설치 및 간단히 사용해 보기
### 5.4 CLI에서 IAM Role 사용해 보기

---

## Chapter 06. S3
- S3 소개
- S3 사용 예
- S3 실습 1 기본 기능 사용해 보기
- S3 버킷 및 파일 삭제
- S3 실습 1 리뷰

---

## Chapter 07. S3의 권한 제어
- S3 권한 제어 유형
- S3 실습 2 퍼블릭으로 권한 설정하기
- ACL을 이용한 권한 제어
- Bucket Policy를 이용한 제어

---

## Chapter 08. S3의 기능과 특징
- CLI로 S3 사용해 보기
- 폴더 동기화 및 ACL 설정하기
- S3 실습 정적 웹 호스팅 기능 사용하기
- multipart upload
- S3 요금과 스토리지 클래스
- 버전관리, 라이프사이클, 일관성

---

## Chapter 09. EC2
- EC2 소개
- MultiAZ와 고가용성
- EC2 관련 서비스들
- VPC-ELB-EC2를 이용한 구성 예제
- EC2 유형과 비용

---

## Chapter 10. EC2 실습 1
- EC2 인스턴스 생성
- EC2 Instance Connect로 접속하기
- EC2 정지 또는 종료하기
- mac 및 linux에서 ssh로 접속하기
- windows에서 ec2 접속하기
- EC2에 elastic-ip 연결하기
- elastic IP 연결 해제

---

## Chapter 11. EC2 실습 2
- EBS 스냅샷 생성
- AMI 생성 및 인스턴스 생성
- ec2-meta-data
- EC2 Role 사용해 보기
- EC2 팁 및 마무리

---

## Chapter 12. VPC
- VPC 소개
- VPC 주요 개념
- CIDR 표기법
- CIDR - Any Address
- CIDR과 서브넷
- CIDR과 VPC 범위

---

## Chapter 13. VPC 실습
- VPC 생성
- subnet 생성 및 라우팅 테이블 연결 확인
- 인터넷 게이트웨이 생성 및 VPC 연결
- public subnet
- public subnet 라우팅 테이블 연결 및 확인
- private subnet과 NAT Gateway
- VPC 마무리
- subnet public ip 자동 할당
- [부록] ec2 private instance에 접속하기
- [부록] nat 인스턴스 설정해 보기

---

## Chapter 14. RDS와 데이터베이스 기초
- RDS 소개 및 특징
- RDS의 장단점
- RDS 생성 전 준비작업
- RDS 생성
- RDS 연결
- GUI tools로 RDS 연결: SSH Tunneling
- RDS 백업
- RDS 확장

---

## Chapter 15. 부록들
- 리소스 정리 및 비용 탐색기
- 퀵랩을 통한 실습자료 살펴보기
- 퀵랩 무료 실습 시작해 보기
- 강의 마무리

---
