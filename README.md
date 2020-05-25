# Python Kafka Workshop

## Prerequisites

### Set PUBLIC_IP (Docker-Compose on Windows only)
```
set PUBLIC_IP=127.0.0.1
```

### Create Topic(s) on Kafka Broker
Create the following topics:
- pm10_raw
- pm10

```
docker exec -ti kafka-1 bash
```

```
kafka-topics --create \
			--if-not-exists \
			--zookeeper zookeeper-1:2181 \
			--topic pm10_raw \
			--partitions 1 \
			--replication-factor 3

kafka-topics --create \
			--if-not-exists \
			--zookeeper zookeeper-1:2181 \
			--topic pm10 \
			--partitions 1 \
			--replication-factor 3
```
### Install confluent-kafka on Jupyter
```
docker exec -ti jupyter bash
```

```
pip install confluent-kafka
pip install confluent-kafka[avro]
```

### Add Avro Schema Registry
Open Schema Registry on Port 28102 and create a new schema ```sensor-raw-value```.


### Import Jupyter Notebooks
Import the following .ipynb files into your Jupyter notebook on Port 28888 and run them:
- Producer.ipynb
- Consumer.ipynb
- Ampel.ipynb

Then create a folder images and copy the 4 "ampel" images into this folder

### Set up StreamSets
Import the File ```DeduplicateSensorRawData.json``` into your Streamsets on localhost:18630 and start the service
