# EC2에 배포할 백엔드(Spring Boot) 서버 프로젝트, 매니페스트 파일 구성하기

---

## 1. Spring Boot 프로젝트 구성

### 1.1 의존성
- Spring Web
- Spring Data JPA
- MySQL

### 1.2 `application-yml`
```yaml
spring:
  datasource:
    url: jdbc:mysql://${DB_HOST}:${DB_PORT}/${DB_NAME}
    username: ${DB_USERNAME}
    password: ${DB_PASSWORD}
    driver-class-name: com.mysql.cj.jdbc.Driver
  jpa:
    hibernate:
      ddl-auto: update # 애플리케이션 실행시점에 JPA 엔티티 설계 - 실제 테이블 상태 비교 후 실제 테이블 변경된 부분만 반영
```

### 1.3 테스트코드 제거
- 실습 편의를 위해 테스트코드 제거

### 1.4 Board
```kotlin
@Entity
@Table(name = "boards")
class Board(
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    var id: Long? = null,

    var title: String,

    var content: String,
)
```


### 1.5 BoardRepository
```kotlin
package com.example.demo

import org.springframework.data.jpa.repository.JpaRepository

interface BoardRepository : JpaRepository<Board, Long>
```
- JPA를 활용해 DB와 연동하고 있는 상태

### 1.6 BoardService
```kotlin
@Service
class BoardService(
    private val boardRepository: BoardRepository
) {

    @Transactional(readOnly = true)
    fun getBoards(): List<Board> {
        return boardRepository.findAll()
    }

    @Transactional
    fun writeBoard(board: Board) {
        boardRepository.save(board)
    }
}
```

### 1.7 BoardController
```kotlin
@RestController
class BoardController(
    private val boardService: BoardService
) {

    @GetMapping("/boards")
    fun getBoards(): List<Board> {
        return boardService.getBoards()
    }

    @PostMapping("/boards")
    fun writeBoard(@RequestBody board: Board) {
        return boardService.writeBoard(board)
    }
}
```

### 1.8 BoardController
```kotlin
@RestController
class BoardController(
    private val boardService: BoardService
) {

    @GetMapping("/boards")
    fun getBoards(): List<Board> {
        return boardService.getBoards()
    }

    @PostMapping("/boards")
    fun writeBoard(@RequestBody board: Board) {
        return boardService.writeBoard(board)
    }
}
```
- `/boards GET` : 게시글 조회 API
- `/boards POST` : 게시글 작성 API

### 1.9 AppController
```kotlin
@RestController
class AppController {

    @GetMapping("/")
    fun home(): String {
        return "Hello, World!"
    }
}
```

### 1.10 Dockerfile
```Dockerfile
FROM amazoncorretto:21-alpine3.20-jdk
COPY build/libs/*SNAPSHOT.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]
```

### 1.10 GitHub 리포지토리
- 이 프로젝트는 아래 리포지토리에 푸시해두었다.
  - `https://github.com/ttasjwi/study-kubernetes-backend`

---

## 2. 매니페스트 파일 준비

### 2.1 시크릿
**spring-secret.yaml**
```yaml
apiVersion: v1
kind: Secret
type: Opaque # 임의의 사용자 정의 데이터를 저장할 때 사용하는 타입

# Secret 기본 정보
metadata:
  name: spring-secret # Secret 이름

# Key, Value 형식으로 값 저장
stringData:
  db-username: "____________________"
  db-password: "____________________"
```

### 2.2 컨피그 맵
**spring-config.yaml**
```yaml
apiVersion: v1
kind: ConfigMap

# ConfigMap 기본 정보
metadata:
  name: spring-config # ConfigMap 이름

# Key, Value 형식으로 설정값 저장
data:
  db-host: "_____________"
  db-port: "3306"
  db-name: "mydb"
```

### 2.3 디플로이먼트
**spring-deployment.yaml**
```yaml
apiVersion: apps/v1
kind: Deployment

# Deployment 기본 정보
metadata:
  name: spring-deployment # Deployment 이름

# Deployment 세부 정보
spec:
  replicas: 3 # 생성할 파드의 복제본 개수
  selector:
    matchLabels:
      app: backend-app # 아래에서 정의한 Pod 중 'app: backend-app'이라는 값을 가진 파드를 선택

  # 배포할 Pod 정의
  template:
    metadata:
      labels: # 레이블 (= 카테고리)
        app: backend-app
    spec:
      containers:
        - name: spring-container # 컨테이너 이름
          image: ________________ # 컨테이너를 생성할 때 사용할 이미지
          ports:
            - containerPort: 8080  # 컨테이너에서 사용하는 포트를 명시적으로 표현
          env:
            - name: DB_HOST
              valueFrom:
                configMapKeyRef:
                  name: spring-config
                  key: db-host
            - name: DB_PORT
              valueFrom:
                configMapKeyRef:
                  name: spring-config
                  key: db-port
            - name: DB_NAME
              valueFrom:
                configMapKeyRef:
                  name: spring-config
                  key: db-name
            - name: DB_USERNAME
              valueFrom:
                secretKeyRef:
                  name: spring-secret
                  key: db-username
            - name: DB_PASSWORD
              valueFrom:
                secretKeyRef:
                  name: spring-secret
                  key: db-password
```

### 2.4 서비스
```yaml
apiVersion: v1
kind: Service

# Service 기본 정보
metadata:
  name: spring-service

# Service 세부 정보
spec:
  type: NodePort # Service의 종류
  selector:
    app: backend-app # 실행되고 있는 파드 중 'app: backend-app'이라는 값을 가진 파드와 서비스를 연결
  ports:
    - protocol: TCP # 서비스에 접속하기 위한 프로토콜
      port: 8080 # 쿠버네티스 내부에서 Service에 접속하기 위한 포트 번호 (Service
      targetPort: 8080 # 매핑하기 위한 파드의 포트 번호
      nodePort: 30000 # 외부에서 사용자들이 접근하게 될 포트 번호
```

### 2.5 GitHun 리포지토리
- 이 매니페스트 파일들은 아래 리포지토리에 푸시해두었다.
    - `https://github.com/ttasjwi/study-kubernetes-manifest`

---

## 3. 코드 살펴보기

### 3.1 스프링 프로젝트
- `/boards GET` : 게시글 조회 API
- `/boards POST` : 게시글 작성 API
- JPA를 활용해 DB와 연동하고 있는 상태
- Docker 이미지로 빌드할 수 있게 `Dockerfile`을 작성해놓은 상태

### 3.2 매니페스트 파일
- Spring Boot 서버를 띄우는 데 필요한 **Deployment, Service, ConfigMap, Secret** 파일들로 구성되어 있음
- `spring-secret.yaml`은 민감한 값이 포함된 파일이므로, 원래라면 `.gitignore`에 추가해서 버전 관리가 되지 않게 만들어야 한다. 
  - 하지만 편의상 Github Repository에 같이 올려두었다.
  - `spring-secret.yaml`은 서버에 따로 전달해서 활용하거나, [SealedSecret](https://coffeewhale.com/sealedsecret)을 활용해서
  관리하는 편이다. (이 외에도 AWS Secrets Manager, Vault 등 시크릿 값을 관리하는 다양한 서비스가 있다.)

---
