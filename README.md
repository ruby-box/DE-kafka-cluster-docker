# Docker kafka cluster
## 구현된 내용
* kafka cluster (kafka1 ~ kafka5)
* zookeeper
* UI for kafka (https://github.com/provectus/kafka-ui)

## 접속 
* UI for kafka : localhost:8081


## 사용법

```sh
cd kafka-cluster
# 컨테이너 기동
docker-compose up -d

# 컨테이너 중지
# docker-compose down

# 브로커 추가
# docker-compose scale kafka=3
```

docker 기타 명령어
```sh
# 컨테이너 프로세스 확인
docker ps

# 컨테이너 로그 확인
docker logs -f kafka1
```

kafka 명령어
```sh
# kafka 컨테이너 접속
docker exec -it kafka1 /bin/bash

# kafka message 컨슈밍
docker-compose exec kafka1 bash
/opt/kafka/bin/kafka-console-consumer.sh \
    --bootstrap-server kafka1:9092 \
    --from-beginning \
    --property print.key=true \
    --topic test1

# kafka message 프로듀싱
docker-compose exec kafka1 bash
/opt/kafka/bin/kafka-console-producer.sh \
    --topic test1 \
    --bootstrap-server kafka1:9092
```
