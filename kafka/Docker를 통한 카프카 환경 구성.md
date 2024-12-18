# Docker를 통한 카프카 환경 구성

---

#### docker-compose-kafka.yml
```yaml
services:
  zookeeper:
    image: confluentinc/cp-zookeeper:${KAFKA_VERSION:-latest}
    container_name: zookeeper
    platform: linux/amd64
    ports:
      - "2181:2181"
    environment:
      # Zookeeper 클러스터 내에서 각 서버를 구분하기 위한 고유 ID. (중복 불가)
      ZOOKEEPER_SERVER_ID: 1

      # 실행포트 2181
      ZOOKEEPER_CLIENT_PORT: 2181

      # Zookeeper의 기본 시간 단위(ms). 세션 타임아웃과 리더-팔로워 동기화에 영향을 줌.
      ZOOKEEPER_TICK_TIME: 2000
      # 초기화 제한 시간
      # 타임아웃 시간은 이전에 지정한 ZOOKEEPER_TICK_TIME 단위로 설정된다.
      # ZOOKEEPER_TICK_TIME을 2000으로 지정했고, ZOOKEEPER_INIT_LIMIT 을 5로 잡았으므로 2000 * 5 = 10000 밀리세컨이 된다. 즉, 10초가 된다.
      ZOOKEEPER_INIT_LIMIT: 5

      # Zookeeper 클러스터 내의 서버 정보
      # Zookeeper 서버 간 통신(클러스터 구성) 및 리더-팔로워 동기화를 위해 필요한 서버 리스트
      # <hostname>:<peer_port>:<election_port> 로 구성
      # <hostname> 은 Zookeeper 서버의 호스트 이름 또는 IP 주소를 의미한다
      # <peer_port> 는  Zookeeper 서버들 간에 데이터 동기화(리더-팔로워 간 데이터 교환)를 위한 포트. 기본적으로 2888을 많이 사용
      # <electrion_port> 는 Zookeeper 클러스터 내에서의 리더를 선출하기 위한 포트로, 기본적으로 3888이 많이 사용된다.
      # 단일 노드 환경에서는 리더-팔로워 관계나 선출 과정이 없으므로, 이 설정은 무시되어도 된다
      ZOOKEEPER_SERVERS: zookeeper:2888:3888

      # 4 letter words : zookeeper 클러스터 관련 정보를 조회하기 위한 명령어
      # telnet, nc 명령을 통해 zookeeper 클라이언트 포트를 통해 전송해 사용할 수 있다
      # 기본적으로는 활성화되어 있지 않은데 설정값으로 다음 설정을 기입해주면 된다.
      # 여기서는 주키퍼 서버가 정상 작동하는지 확인하기 위한 ruok 명령을 전달
      KAFKA_OPTS: "-Dzookeeper.4lw.commands.whitelist=ruok"

    # 데이터를 저장할 외부 볼륨 경로 설정.
    # /var/lib/zookeeper/data: Zookeeper 데이터 디렉토리.
    # /var/lib/zookeeper/log: Zookeeper 트랜잭션 로그 디렉토리.
    volumes:
      - zookeeper-data:/var/lib/zookeeper/data
      - zookeeper-log:/var/lib/zookeeper/log

    # 사용할 네트워크. 환경 변수 GLOBAL_NETWORK 값을 사용하며, 기본값은 kafka.
    networks:
      - ${GLOBAL_NETWORK:-kafka}


  kafka:
    image: confluentinc/cp-kafka:${KAFKA_VERSION}
    container_name: kafka
    platform: linux/amd64
    # zookeeper 컨테이너가 먼저 실행되어야 한다
    depends_on:
      - zookeeper

    ports:
      - "19092:19092"

    environment:

      # Kafka 클러스터 내에서 각 서버를 구분하기 위한 고유 ID. (중복 불가)
      KAFKA_BROKER_ID: 1

      # zookeeper 서비스명, 포트
      # zookeeper 서비스를 도커 네트워크에서 찾아 인식한다, 그리고 그 내부포트 2181 로 접근
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181

      # kafka 브로커가 외부 클라이언트에게 제공하는 주소 및 포트를 정의
      # external: 외부 클라이언트가 kafka 브로커에 연결할 때 사용할 주소, localhost:19092 에 카프카를 게시하여 외부에서 접근가능하게 한다.
      # internal: 내부 클러스터 통신을 위한 주소. 클러스터 내부에서 다른 브로커들이 사용하기 위한 로컬 주소
      # 우리는 kafka 이름으로 서비스를 등록해뒀고, 도커 네트워크 상의 컨테이너들은 kafka 이름의 서비스를 찾아 9092 포트로 접근할 수 있다.
      KAFKA_ADVERTISED_LISTENERS: internal://kafka:9092,external://localhost:19092

      # 각 리스너 이름 및 보안 프로토콜 지정
      # 예) internal:PLAINTEXT -> internal 리스너는 PLAINTEXT 보안 프로토콜을 사용한다
      KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: internal:PLAINTEXT,external:PLAINTEXT

      # 브로커들 간의 통신은 internal 리스너를 통해 이루어진다
      KAFKA_INTER_BROKER_LISTENER_NAME: internal

    volumes:
      - kafka-data:/var/lib/kafka/data

    networks:
      - ${GLOBAL_NETWORK:-kafka}

networks:
  kafka-network:
    driver: bridge

volumes:
  zookeeper-data:
    driver: local
  zookeeper-log:
    driver: local
  kafka-data:
    driver: local
```

---

#### `.env`
```properties
KAFKA_VERSION=7.1.2
GLOBAL_NETWORK=kafka-network
```
- `KAFKA_VERSION` : 카프카 버전
- `GLOBAL_NETWORK` : 네트워크명

---

####  실행
```shell
docker-compose -f dokcer-compose-kafka.yml up -d
docker logs zookeeper
docker logs kafka
```
```shell
$ docker logs zookeeper
===> User
uid=1000(appuser) gid=1000(appuser) groups=1000(appuser)
===> Configuring ...
===> Running preflight checks ...
===> Check if /var/lib/zookeeper/data is writable ...
===> Check if /var/lib/zookeeper/log is writable ...
===> Launching ...
===> Printing /var/lib/zookeeper/data/myid
1===> Launching zookeeper ...
[2024-12-18 04:38:16,818] INFO Reading configuration from: /etc/kafka/zookeeper.properties (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
[2024-12-18 04:38:16,827] INFO clientPortAddress is 0.0.0.0:2181 (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
[2024-12-18 04:38:16,827] INFO secureClientPort is not set (org.apache.zookeeper.server.quorum.QuorumPeerConfig)
# 생략
```

---

#### 작동 확인
```shell
$ docker exec zookeeper sh -c "echo ruok | nc localhost 2181"
imok
```

```shell
$ docker exec kafka kafka-topics --bootstrap-server kafka:9092 --create --topic welcome-topic
Created topic welcome-topic.
```

---

#### 중단
```shell
docker rm -f kafka
docker rm -f zookeeper
```

또는

```shell
docker-compose -f docker-compose down
```

---

- 참고자료: [[Kafka] Docker Compose 를 이용하여 Single Broker 구성하기](https://devocean.sk.com/blog/techBoardDetail.do?ID=164007)

---
