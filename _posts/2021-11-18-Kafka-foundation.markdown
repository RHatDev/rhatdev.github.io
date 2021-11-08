---
layout: post
title:  "Apache Kafka Foundation!"
date:   2021-11-18 09:34:00 -0400
categories: apache kafka
---
Following is based on a course `Apache Kafka Essential Training: Getting Started` by `Kumaran Ponnambalam`.

### What is Apache Kafka
- Kafka is an event streaming platform.
- It is open source with commercial options.
- It is the most poplular messaging platform.
- It plays a critical role in big data. 

### Kafka Single Node 

I have tested this on podman but you can use docker. Here is the docker-compose file:

{% highlight yaml %}

version: '2'
services:

#Zookeeper Service.
  zookeeper:
    image: 'bitnami/zookeeper:latest'
    restart: "no"
    ports:
      - '2181:2181'
    environment:
      - ALLOW_ANONYMOUS_LOGIN=yes
    container_name: zookeeper

#Kafka Service
  kafka:
    image: 'bitnami/kafka:latest'
    restart: "no"
    ports:
      - '9092:9092'
      - '29092:29092'
      
    environment:
      - KAFKA_CFG_LISTENER_SECURITY_PROTOCOL_MAP=INTERNAL:PLAINTEXT,EXTERNAL:PLAINTEXT
      - KAFKA_CFG_LISTENERS=INTERNAL://:29092,EXTERNAL://:9092
      - KAFKA_CFG_ADVERTISED_LISTENERS=INTERNAL://kafka:29092,EXTERNAL://localhost:9092
      - KAFKA_CFG_ZOOKEEPER_CONNECT=zookeeper:2181
      - KAFKA_INTER_BROKER_LISTENER_NAME=INTERNAL
      - ALLOW_PLAINTEXT_LISTENER=yes
      
    container_name: kafka-broker
    
    depends_on:
      - "zookeeper"
    
{% endhighlight %}

Install podman and podman compose

{% highlight bash %}
sudo dnf install podman
curl -o /usr/local/bin/podman-compose https://raw.githubusercontent.com/containers/podman-compose/devel/podman_compose.py
chmod +x /usr/local/bin/podman-compose
{% endhighlight %}

Save the above yaml file as `kafka-single-node.yml` and run `podman-compose -f kafka-single-node.yml up -d` command in that folder, which will start a container for zookeeper and and one caintainer for kafka-broker.

### Zookeeper [TODO]

### Kafka Broker [TODO]
