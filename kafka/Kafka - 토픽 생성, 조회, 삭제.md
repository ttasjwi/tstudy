# Kafka - 토픽 생성, 조회, 삭제

---

### 카프카 서버 기동
```shell
cd ~/docker/kafka-compose
docker-compose -f docker-compose-kafka.yml up zookeeper
```
```shell
cd ~/docker/kafka-compose
docker-compose -f docker-compose-kafka.yml up kafka
```

---

### 토픽 명령 개요
- 토픽 관련 명령은 `kafka-topics` 명령을 통해 수행한다.
- 이 때 `--bootstrap-server` 명령을 통해 어느 브로커에게 명령할지 지정해야한다.
  - 예) `kafka-topics --bootstrap-server kafka:9092 ...`
- 특정 토픽에 대한 명령을 하기 위해서는 `--topic <토픽명>` 을 통해 토픽을 지정해야한다.
  - 예) `kafka-topics --bootstrap-server kafka:9092 --create --topic hello-topic`

---

### 토픽 생성
```shell
docker exec kafka kafka-topics --bootstrap-server kafka:9092 --create --topic test_topic_01
  
# 파티션 3개로 구성된 토픽 생성
docker exec kafka kafka-topics --bootstrap-server kafka:9092 --create --topic test_topic_02 --partitions 3

# 파티션 3개, 복제 2개로 구성된 토픽 생성(실패 : 두개 이상의 브로커 필요)
docker exec kafka kafka-topics --bootstrap-server kafka:9092 --create --topic test_copic_02 --partitions 3 --replication-factor 2
```
- `--create` 옵션을 통해 토픽을 생성할 수 있다.
- `--topic` : 특정 토픽에 대한 명령을 하기 위해서는 `--topic <토픽명>` 을 통해 토픽을 지정해야한다.
- `--partition` : 파티션의 갯수
  - 이 속성을 지정하지 않으면 server.properties 에서 지정된 기본값(1개)을 따른다.
- `--replication-factor` : 복제본의 갯수 (이 속성을 지정하려면 2개 이상의 브로커를 기동해야한다.)

#### 토픽 생성 설정 변경
```shell
docker exec -it kafka bash
```
```shell
cat /etc/kafka/server.properties | grep num.partitions
num.partitions=1
```
- 카프카 경로의 `./etc/kafka/server.properties` 에서 토픽 생성시의 기본 파티션 갯수를 변경할 수 있다.
- docker 기준으로는 루트 경로 아래(`/etc/kafka/server.properties`)에서 이 값을 확인할 수 있다.

---

### 토픽 목록 조회
```shell
docker exec kafka kafka-topics --bootstrap-server kafka:9092 --list

test_topic_01
test_topic_02
```
- `--list` 옵션을 통해 토픽 목록을 볼 수 있다.

---

### 토픽 단건 조회
```shell
docker exec kafka kafka-topics --bootstrap-server kafka:9092 --describe --topic test_topic_02             

Topic: test_topic_02    TopicId: 0nITHH10Tr2PnBu9sxPxhg PartitionCount: 3       ReplicationFactor: 1    Configs:
        Topic: test_topic_02    Partition: 0    Leader: 1       Replicas: 1     Isr: 1
        Topic: test_topic_02    Partition: 1    Leader: 1       Replicas: 1     Isr: 1
        Topic: test_topic_02    Partition: 2    Leader: 1       Replicas: 1     Isr: 1
```
- `--describe` 옵션을 통해 단건의 토픽에 대해 상세 정보를 조회할 수 있다.
- `--topic` : 특정 토픽에 대한 명령을 하기 위해서는 `--topic <토픽명>` 을 통해 토픽을 지정해야한다.
- 파티션은 몇 개 있는지, 복제본은 몇 개 있는지, ...

---

### 토픽 삭제
```shell
kafka-topics --bootstrap-server localhost:9092 --delete --topic test_topic_02
```
- `--delete` 옵션을 통해 토픽을 삭제할 수 있다.
- `--topic` : 특정 토픽에 대한 명령을 하기 위해서는 `--topic <토픽명>` 을 통해 토픽을 지정해야한다.

---

### 토픽별 로그
```shell
docker exec -it kafka bash
ls /var/lib/kafka/data -al

total 44
drwxrwxr-x 6 appuser root    4096 Dec 20 08:50 .
drwxrwx--- 3 appuser root    4096 Jun 24  2022 ..
-rw-r--r-- 1 appuser appuser    0 Dec 19 00:39 .lock
-rw-r--r-- 1 appuser appuser    4 Dec 20 08:33 cleaner-offset-checkpoint
-rw-r--r-- 1 appuser appuser    4 Dec 20 08:50 log-start-offset-checkpoint
-rw-r--r-- 1 appuser appuser   88 Dec 20 08:19 meta.properties
-rw-r--r-- 1 appuser appuser   76 Dec 20 08:50 recovery-point-offset-checkpoint
-rw-r--r-- 1 appuser appuser   76 Dec 20 08:50 replication-offset-checkpoint
drwxr-xr-x 2 appuser appuser 4096 Dec 20 08:20 test_topic_01-0
drwxr-xr-x 2 appuser appuser 4096 Dec 20 08:28 test_topic_02-0
drwxr-xr-x 2 appuser appuser 4096 Dec 20 08:28 test_topic_02-1
drwxr-xr-x 2 appuser appuser 4096 Dec 20 08:28 test_topic_02-2
```
- 앞서 생성한 토픽들에 대해, 로그들이 디렉토리 단위로 모여져 있다.
  - 토픽-파티션마다 디렉토리가 구성된다.

```shell
ls /var/lib/kafka/data/test_topic_01-0 -al
total 16
drwxr-xr-x 2 appuser appuser     4096 Dec 20 08:20 .
drwxrwxr-x 6 appuser root        4096 Dec 20 08:51 ..
-rw-r--r-- 1 appuser appuser 10485760 Dec 20 08:20 00000000000000000000.index
-rw-r--r-- 1 appuser appuser        0 Dec 20 08:20 00000000000000000000.log
-rw-r--r-- 1 appuser appuser 10485756 Dec 20 08:20 00000000000000000000.timeindex
-rw-r--r-- 1 appuser appuser        8 Dec 20 08:20 leader-epoch-checkpoint
-rw-r--r-- 1 appuser appuser       43 Dec 20 08:20 partition.metadata
```
- 이 경로 안에는 로그를 비롯해 여러가지 파일들이 모여져 있는 것을 볼 수 있다.

---
