# 백엔드(Spring Boot) 서버 3개 띄워보기
> 실제 서비스를 운영하다보면 트래픽이 증가해서 서버가 버벅거리는 경우가 생긴다.  
> 이 때는 서버를 수평적 확장(서버의 개수를 늘리는 방식)을 통해 해결한다.  
> 이런 상황을 가정해 백엔드 서버인 Spring Boot 서버를 3대로 늘려보자.

---

## 1. 스프링부트 프로젝트 작성

### 1.1 API 작성
```kotlin
@RestController
class AppController {
    
    @GetMapping("/")
    fun hello(): String {
        println("Hello, World!") // 추후 디버깅용
        return "Hello, World!"
    }
}
```
- 기존에 만들어뒀던 Spring Boot 프로젝트에서, AppController 부분만 수정
- API 호출 시 내부에서 `Hello, World!` 를 출력

### 1.2 실행 확인
![example-spring-boot-pod-1](./imgs/example-spring-boot-pod-1.png)

- `http://localhost:8080/` 로 요청을 보내보면 성공적으로 문자열 응답이 오는 것을 확인

### 1.3 빌드
```shell
./gradlew clean build
```

### 1.4 빌드 결과물 확인
```shell
$ cd build/libs
$ ls -al
total 25228
drwxr-xr-x 1 ttasjwi 197121        0  2월 18 14:39 ./
drwxr-xr-x 1 ttasjwi 197121        0  2월 18 14:39 ../
-rw-r--r-- 1 ttasjwi 197121 25824047  2월 18 14:39 demo-0.0.1-SNAPSHOT.jar
-rw-r--r-- 1 ttasjwi 197121     3265  2월 18 14:39 demo-0.0.1-SNAPSHOT-plain.jar
```

---

## 2. 도커 이미지 생성

### 2.1 Dockerfile 작성
```Dockerfile
FROM amazoncorretto:21-alpine3.20-jdk
COPY build/libs/*SNAPSHOT.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]
```
- 앞에서 jar 파일 빌드를 해놔야한다.

### 2.2 Dockerfile 을 기반으로 도커 이미지 빌드
```shell
docker build -t spring-server .
```

### 2.3 도커 이미지 확인
```shell
docker image ls
```

---

## 3. 파드 매니페스트 파일 작성
**spring-pod.yaml**
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: spring-pod-1
spec:
  containers:
    - name: spring-container
      image: spring-server
      ports:
        - containerPort: 8080
      imagePullPolicy: IfNotPresent

---

apiVersion: v1
kind: Pod
metadata:
  name: spring-pod-2 # 이름이 겹쳐선 안 됨
spec:
  containers:
    - name: spring-container
      image: spring-server
      ports:
        - containerPort: 8080
      imagePullPolicy: IfNotPresent

---

apiVersion: v1
kind: Pod
metadata:
  name: spring-pod-3 # 이름이 겹쳐선 안 됨
spec:
  containers:
    - name: spring-container
      image: spring-server
      ports:
        - containerPort: 8080
      imagePullPolicy: IfNotPresent
```
- `---` 로 구분을 하면 한 매니페스트 파일 내에서 각각의 설정을 읽어서 적용한다.

---

## 4. 매니페스트 파일을 기반으로 파드(Pod) 생성하기
```shell
kubectl apply -f spring-pod.yaml
```

---

## 5. 파드 생성 확인
```shell
$ kubectl get pods
NAME           READY   STATUS    RESTARTS   AGE
spring-pod-1   1/1     Running   0          7s
spring-pod-2   1/1     Running   0          7s
spring-pod-3   1/1     Running   0          7s
```

---

## 6. 한계
- 3개의 Spring Boot 서버를 띄우는 데 성공했다. 
- 하지만 서버가 3개여서 망정이지 만약 100개의 서버를 띄워야 한다면 불편하지 않을까? 그리고 서비스를 운영하다보면 시간, 계절, 이벤트 등에 
따라 트래픽은 시시각각 변한다. 그럴 때마다 트래픽에 맞게 서버의 대수를 바꿔야 한다면 아주 불편할 것이다.
- 이런 불편함을 해결해주는 쿠버네티스의 기능이 **디플로이먼트(Deployment)** 이다. 이어서 디플로이먼트에 대해 알아보자.

---
