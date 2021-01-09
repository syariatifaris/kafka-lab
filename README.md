
# Kafka Lab

Setup Kafka infrastructure for local development using Docker.

You can find the complete & original documentation / instructions for this repo at [Build Your Own Demo - confluent.io](https://docs.confluent.io/current/tutorials/build-your-own-demos.html?utm_source=github&utm_medium=demo&utm_campaign=ch.examples_type.community_content.cp-all-in-one)

## A. Run Locally

To run the Kafka infrastructure, run: 

```sh
docker-compose up
```
Use and connect your client to  **localhost:9092** to publish / subscribe the message. 

## B. Installing Kafka Console

For the development purpose you may need to access the running Kafka infrastruture from your CLI. For instance, you need to publish or subscribe a message to / for a certain topic without creating a client app. 

1. Download the kafka at [Apache Kafka Official Site](https://www.apache.org/dyn/closer.cgi?path=/kafka/2.7.0/kafka_2.13-2.7.0.tgz).

2. Extract the folder to a certain location:
```sh
tar -xfv kafka_[version].tgz
```

3. To use the console app, navigate to **bin** folder

## C. Using Kafka Console

Belows are some Kafka basic operations that are commonly used for development purpose.  

### I. Creating a Topic

To create a topic, use this command:

```sh
./kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic [topic_name]
```

PS: Replication factor should not be greater than the number of brokers. 

### II. List All Topic

To list all topic use this command:

```sh
./kafka-topics.sh --list --zookeeper localhost:2181
```

### III. Publishing a Message to Topic

To publish a message to topic, simply use this command:

```
 ./kafka-console-producer.sh --broker-list localhost:9092 --topic [topic_name]
```

After executing the command above, the console will asks you to input the message that want to be send to the topic. 

### IV. Consuming a Message from A Topic

To consume a message from a certain topic, run: 

```sh
./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic [topic_name] --from-beginning

```

Use --from-beginning to read all the data. 