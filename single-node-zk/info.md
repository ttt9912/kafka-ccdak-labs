# Connect to Kafka

List Compose Projects

```
docker compose ls
```

Go to Project folder

```
cd /Users/thomastschachtli/dev/workspaces/kafka-ccdak-labs/single-node-zk
```

List services

```
docker compose ps
```

Connect to service (Kafka CLI)

```
docker compose exec -it kafka /bin/bash
```

# Alternative: start new kafka in this network

```
docker network ls
```

```
docker run -it --net=single-node-zk_default --rm  confluentinc/cp-kafka:latest /bin/bash
```

# Kafka Commands

```
/bin/kafka-topics --bootstrap-server localhost:9092 --list
```

```
/bin/kafka-topics --bootstrap-server localhost:9092 --create --topic sensor --partitions 1 --replication-factor 1 --if-not-exists
```

```
/bin/kafka-topics --bootstrap-server localhost:9092 --describe --topic sensor
```