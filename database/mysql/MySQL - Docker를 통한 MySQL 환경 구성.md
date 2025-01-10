# MySQL - Docker를 통한 MySQL 환경 구성
- 사전 준비: Docker 설치

---

### MySQl 이미지 풀링
```shell
docker pull mysql:8.0.40-debian;
```
- MySQL 이미지를 풀링해온다.

---

### 커스텀 MySQL 이미지 구성
```shell
mkdir -p ./tmp
echo "FROM mysql:8.0.40-debian" > ./tmp/Dockerfile
echo "RUN apt-get update && apt-get install -y locales" >> ./tmp/Dockerfile
echo "RUN localedef -f UTF-8 -i ko_KR ko_KR.UTF-8" >> ./tmp/Dockerfile
echo "ENV LC_ALL ko_KR.UTF-8" >> ./tmp/Dockerfile
docker build -t mysql:ttasjwi ./tmp/
rm -rf ./tmp
```
- 로케일 정보를 ko_KR.UTF-8 로 설정한 커스텀 도커 이미지이다.

```shell
$ docker images;
REPOSITORY                        TAG             IMAGE ID       CREATED         SIZE
mysql                             ttasjwi         44234f27d1cc   5 minutes ago   649MB
mysql                             8.0.40-debian   93f1a2fa0508   2 weeks ago     610MB
```
- 위 과정을 거치면 커스텀한 MySQL 이미지가 생성된다.

---

### 도커 볼륨 생성
```shell
$ docker volume create --name mysql-data;
mysql-data
$ docker volume create --name mysql-conf;
mysql-conf
$ docker volume create --name mysql-initdb;
mysql-initdb
```

---

### 도커 컴포즈 파일 생성
```yaml
services:
  mysql:
    image: mysql:ttasjwi
    container_name: mysql
    ports:
      - "3306:3306"
    environment:
      - MYSQL_ROOT_PASSWORD=db1004
    restart: unless-stopped
    command:
      - --character-set-server=utf8mb4
      - --collation-server=utf8mb4_unicode_ci
    volumes:
      - mysql-data:/var/lib/mysql
      - mysql-conf:/etc/mysql/conf.d
      - mysql-initdb:/docker-entrypoint-initdb.d

volumes:
  mysql-data:
    external: true
  mysql-conf:
    external: true
  mysql-initdb:
    external: true
```
- 적절한 위치에 파일을 생성한다. 나의 경우 `~/docker/mysql-compose/docker-compose-mysql.yml` 파일을 생성했다.

---

### 도커 컴포즈 실행
```shell
docker-compose -f ~/docker/mysql-compose/docker-compose-mysql.yml up -d
```

---

### MySQL 컨테이너 접속
```shell
docker exec -it mysql bash
```

---

### MySQL 사용자 생성 및 권한 부여
- MySQL에 접속
    ```shell
    mysql -uroot -p
    ## 비밀번호 입력
    ```
- 사용자 생성
    ```shell
    CREATE user '이름'@'호스트'
    IDENTIFIED BY '패스워드';
    ```
- 권한 부여
    ```shell
    GRANT ALL ON *.* TO '사용자이름'@'호스트';
    FLUSH PRIVILEGES;
    ```

---
