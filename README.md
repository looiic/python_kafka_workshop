# Python Kafka Workshop

## Prerequisites

### Set PUBLIC_IP (Docker-Compose on Windows only)
```
set PUBLIC_IP=127.0.01
```

### Create Topic(s) on Kafka Broker
Create the following topics:
- sensor-raw

```
docker exec -ti kafka-1 bash
```

```
kafka-topics --create \
			--if-not-exists \
			--zookeeper zookeeper-1:2181 \
			--topic sensor-raw \
			--partitions 1 \
			--replication-factor 3
```
### Install confluent-kafka on Jupyter
```
docker exec -ti jupyter bash
```

```
pip install confluent-kafka
```

### Add Avro Schema Registry
Open Schema Registry on Port 28102 and create a new schema ```sensor-raw-value```.
