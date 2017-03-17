This a end-to-end log centralizer powered by the ELK stask.

Embedded containers
-
 1. [Filebeat](https://www.elastic.co/products/beats/filebeat) - An agent to poll logs
 2. [Logstash-Forwarder](https://github.com/elastic/logstash-forwarder) - An other agent to poll logs
 3. [Logstash](https://www.elastic.co/products/logstash) - The collector / analyzer / parser solution
 4. [Kafka](http://kafka.apache.org) - The queueing solution for logs
 5. [ZooKeeper](https://zookeeper.apache.org/) - The cluster on which Kafka is running
 6. [ElasticSearch](https://www.elastic.co/products/elasticsearch) - The indexing engine
 7. [Kibana](https://www.elastic.co/products/kibana) - The visualization / dashboard tool for ElasticSearch
 8. [Kafka Manager](https://github.com/yahoo/kafka-manager) - The Kafka cluster web manager

How it works
-
There are 2 agent types :

 - Filebeat
 - Logstash-Forward

These agents push logs to a Logstasth shipper filling a Kafka queue (one type of log for one topic). 
A Logstash indexer polls the Kafka topics indexing logs into a ElasticSearch.

A short schema :
```
Agent -> Logstach shipper -> Kafka <- Logstash indexer -> ElasticSearch
```

Tools access
-
Kibana is available at http://localhost:5601.
Kafka Manager is available at http://localhost:9000

 
