# Installation of Zookeeper

This installation of Zookeeper will store the configuration in `/usr/local/zookeeper` and its data in `/var/lib/zookeeper`. 

Assume you have installed Java JDK and it will be in environment variable `JAVA_HOME`
```
# tar -zxf zookeeper-3.4.6.tar.gz
# mv zookeeper-3.4.6 /usr/local/zookeeper
# mkdir -p /var/lib/zookeeper
# cat > /usr/local/zookeeper/conf/zoo.cfg << EOF
> tickTime=2000
> dataDir=/var/lib/zookeeper
> clientPort=2181
> EOF
# export JAVA_HOME=/usr/lib/jvm/default-java
# /usr/local/zookeeper/bin/zkServer.sh start

JMX enabled by default
Using config: /usr/local/zookeeper/bin/../conf/zoo.cfg
Starting zookeeper ... STARTED
```

> NB: if cannot start zookeeper you maybe want to change the owner of `/var/lib/zookeeper`. Use this command to change the owner
`sudo chown -R $USER /var/lib/zookeeper`

To assure that your zookepeer able to run as a standalone server, we will do `telnet` to send simple message which is `srvr`

```
# telnet localhost 2181
Trying ::1...
Connected to localhost.
Escape character is '^]'.
srvr
Zookeeper version: 3.4.6-1569965, built on 02/20/2014 09:09 GMT
Latency min/avg/max: 0/0/0
Received: 1
Sent: 0
Connections: 1
Outstanding: 0
Zxid: 0x0
Mode: standalone
Node count: 4
Connection closed by foreign host.
#
```

# Installation of Kafka Broker
```
# tar -zxf kafka_2.11-0.9.0.1.tgz
# mv kafka_2.11-0.9.0.1 /usr/local/kafka
# mkdir /tmp/kafka-logs
# export JAVA_HOME=/usr/java/jdk1.8.0_51
# /usr/local/kafka/bin/kafka-server-start.sh -daemon /usr/local/kafka/config/server.properties
#
```

```
# /usr/local/kafka/bin/kafka-topics.sh --create --zookeeper localhost:2181
--replication-factor 1 --partitions 1 --topic test
Created topic "test".
# /usr/local/kafka/bin/kafka-topics.sh --zookeeper localhost:2181
--describe --topic test
Topic:test
PartitionCount:1
ReplicationFactor:1
Configs:
Topic: test
Partition: 0
Leader: 0
Replicas: 0
Isr: 0
#
```