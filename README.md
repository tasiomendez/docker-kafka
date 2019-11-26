# Kafka in Docker

This repository provides everything you need to run Kafka in Docker.

The main issue of running Kafka in Docker is that it depends on Zookeeper. For convinience,
this one provides two Docker containers: one running Zookeeper and another one running
a kafka server with the option of creating topics.

The version of the deployments are 2.11 for Scala and 2.3.1 for Kafka. All of them
can be obtained in the [official webpage](https://kafka.apache.org/downloads).

## Run

Zookeeper listens on the port `2181`, while Kafka is listening on `9092`.

```bash
docker-compose up
```

## Build from Source

```bash
docker build -t tasiomendez/kafka .
```

Once the Docker image is created, before running it, is needed to run
an instance of Zookeeper.

```bash
docker run --name zookeeper -p 2181:2181 -d zookeeper:latest
docker run --name kafka-server -p 9092:9092 --env ZOOKEEPER_HOST="localhost:2181" tasiomendez/kafka
```
