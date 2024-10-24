# Kafka (using Docker Compose)

Spinning up a Kafka broker with minimal effort

## Setup

- `docker` - https://docs.docker.com/get-docker/
- `docker-compose` - https://docs.docker.com/compose/install/

# Misc links

- Kafka without Zookeeper i.e. KRaft - https://github.com/confluentinc/cp-all-in-one/tree/7.0.1-post/cp-all-in-one-kraft
- Kafka cluster - https://blog.exxeta.com/en/2021/05/20/kafka-cluster-setup-with-docker-and-docker-compose/
- Kakfa single - https://code.parts/2020/06/21/kafka-docker-compose-yml/

## Commands

1. Start Zookeeper and a single broker (ID 1), as well as a couple of UIs

**NOTE: Use `-d` to run in the background and the `docker-compose down` to stop it**

```bash
docker-compose up
```

2. Navigate to either [Kafka-UI](http://localhost:8080) or [Kafdrop](http://localhost:9001)

3. Remove the stopped containers (optional)

```bash
docker-compose rm
```

## Misc commands

```bash
docker-compose exec kafka kafka-topics.sh --bootstrap-server localhost:9092 --delete --topic test2
docker-compose exec kafka kafka-topics.sh --list --bootstrap-server localhost:9092
docker-compose exec kafka kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 20 --topic test2
kcat -L -b localhost:9092
```

## Ports

- Zookeeper - localhost:2181
- Broker (ID 1) - localhost:9092

## Produce and consume a message

- Produce a message of `Hello World` to the topic `testing`
  22181

```bash
echo "Hello World" | kcat -P -b localhost:9092 -t testing
```

- Consume the message from the topic `testing`

```bash
kcat -t testing -b localhost:9092
```

## Running Kafka scripts from the Broker container

```bash
docker-compose exec kafka kafka-topics.sh --list --bootstrap-server localhost:9092
```
