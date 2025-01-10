# Redis - Docker를 통한 Redis 환경 구성
- 사전 준비: Docker 설치

---

### Redis 이미지 풀링
```shell
docker pull redis:7.4.1;
```
- Redis 이미지를 풀링해온다.

---

### 도커 볼륨 생성
```shell
docker volume create --name redis-data
redis-data

docker volume create --name redis-conf
redis-conf
```

---

### 도커 컴포즈 파일 생성

```yaml
services:
  redis:
    image: redis:7.4.1
    container_name: redis
    ports:
      - "6379:6379"
    volumes:
      - redis-data:/data
      - redis-conf:/usr/local/conf/redis.conf
    restart: always

volumes:
  redis-data:
    external: true
  redis-conf:
    external: true
```
- 적절한 위치에 파일을 생성한다. 나의 경우 `~/docker/redis-compose/docker-compose-redis.yml` 파일을 생성했다.

---

### 도커 컴포즈 실행
```shell
docker-compose -f ~/docker/redis-compose/docker-compose-redis.yml up -d
```

---

### Redis 컨테이너 접속
```shell
docker exec -it redis bash
```

---

### Redis 실행
```shell
redis-cli
127.0.0.1:6379>
```

---
