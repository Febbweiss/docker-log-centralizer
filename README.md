This a end-to-end log centralizer powered by the ELK stask.

Embedded containers
-
 * [Filebeat](https://www.elastic.co/products/beats/filebeat) - An agent to poll logs
 * [Logstash-Forwarder](https://github.com/elastic/logstash-forwarder) - An other agent to poll logs
 * [rsyslog](http://www.rsyslog.com/) - A standard Linux log manager
 * [Logstash](https://www.elastic.co/products/logstash) - The collector / analyzer / parser solution
 * [Kafka](http://kafka.apache.org) - The queueing solution for logs
 * [ZooKeeper](https://zookeeper.apache.org/) - The cluster on which Kafka is running
 * [ElasticSearch](https://www.elastic.co/products/elasticsearch) - The indexing engine
 * [Kibana](https://www.elastic.co/products/kibana) - The visualization / dashboard tool for ElasticSearch
 * [Kafka Manager](https://github.com/yahoo/kafka-manager) - The Kafka cluster web manager
 * [Apache log generator](https://github.com/Febbweiss/docker-apache-log-generator) - A container generating fake apache logs
 * [Random log generator](https://hub.docker.com/r/davidmccormick/random_log_generator) - A container generating text logs (Star Wars quotes)
 * [Java log generator](https://github.com/Febbweiss/docker-java-log-generator) - A container generating Java logs (with exception stack trace)

How it works
-
There are 3 agent types :

 - Filebeat
 - Logstash-Forward
 - rsyslog

These agents push logs (from the generators) to a Logstasth shipper filling a Kafka queue (one type of log for one topic). 
A Logstash indexer polls the Kafka topics indexing logs into a ElasticSearch.

A short schema :
```
Agent -> Logstach shipper -> Kafka <- Logstash indexer -> ElasticSearch
```

Tools access
-
Kibana is available at http://localhost:5601.
Kafka Manager is available at http://localhost:9000

 
