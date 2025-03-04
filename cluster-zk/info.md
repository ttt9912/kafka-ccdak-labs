# Start Kafka CLI

```
docker run -it --net=host --rm  confluentinc/cp-kafka:latest /bin/bash
```

# Kafka Commands

```
/bin/kafka-topics --bootstrap-server localhost:19092 --list
```

```
/bin/kafka-topics --bootstrap-server localhost:19092 --create \
--topic sensor --partitions 2 --replication-factor 3 --if-not-exists
```

```
/bin/kafka-topics --bootstrap-server localhost:19092 --describe --topic sensor
```
## Producer

```
seq 42 | sed 's/\([0-9]\+\)/\1:\1/g' | /bin/kafka-console-producer --broker-list localhost:19092 --topic sensor  --property parse.key=true --property key.separator=: && echo 'Produced 42 messages.'
```

## Consumer

```
/bin/kafka-console-consumer --bootstrap-server localhost:19092,localhost:29092,localhost:39092,localhost:49092,localhost:59092 --from-beginning --property print.key=true --property key.separator=":" --topic sensor
```