# (예제) 백엔드(Nest.js) 서버를 파드(Pod)로 띄워보기

---

## 1. Nest.js 프로젝트 작성

### 1.1 Nest.js 프로젝트 생성
```shell
# nest CLI 설치
npm i -g @nestjs/cli

# nest new {프로젝트명}
nest new nest-server
```

### 1.2 Nest.js 프로젝트 실행
```shell
npm i
npm run start
```
![example-nest-js-pod-1](./imgs/example-nest-js-pod-1.png)

---

## 2. 도커 이미지 생성

### 2.1 Dockerfile 작성
```Dockerfile
FROM node

WORKDIR /app

# 현 위치 파일들을 컨테이너의 /app 로 복사
COPY . .

RUN npm install

RUN npm run build

# 문서화 역할 (3000번 포트에서 실행됨 명시)
EXPOSE 3000

ENTRYPOINT [ "node", "dist/main.js" ]
```

### 2.2 `.dockerignore`
```shell
node_modules
```
- 로컬의 `node_modules` 가 복사되지 않도록 함


### 2.3 Dockerfile 을 기반으로 도커 이미지 빌드
```shell
docker build -t nest-server .
```

### 2.4 도커 이미지 확인
```shell
$ docker image ls
REPOSITORY                                TAG                                                                           IMAGE ID       CREATED         SIZE
nest-server                               latest                                                                        3427d4f413ba   5 seconds ago   1.42GB
```

---

## 3. 파드 매니페스트 파일 작성
**nest-pod.yaml**
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nest-pod
spec:
  containers:
    - name: nest-container
      image: nest-server
      ports:
        - containerPort: 3000
      imagePullPolicy: IfNotPresent
```

---

## 4. 매니페스트 파일을 기반으로 파드(Pod) 생성하기
```shell
kubectl apply -f nest-pod.yaml
```

---

## 5. 파드 생성 확인
```shell
$ kubectl get pods
NAME       READY   STATUS    RESTARTS   AGE
nest-pod   1/1     Running   0          31s                                                            ae196f6d08c0   16 minutes ago   342MB
```

---

## 6. 포트 포워딩으로 Nest.js 서버가 실행됐는 지 확인
```shell
$ kubectl port-forward pod/nest-pod 3000:3000
Forwarding from 127.0.0.1:3000 -> 3000
Forwarding from [::1]:3000 -> 3000
```
![example-nest-js-pod-1.png](./imgs/example-nest-js-pod-1.png)

---

## 7. 파드 삭제
```shell
kubectl delete pod nest-pod
kutectl get pods
```

---
