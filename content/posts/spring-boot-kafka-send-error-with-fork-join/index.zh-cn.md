---
title: "spring boot使用Java并行流发送kafka消息报错"
date: 2023-04-05T23:15:22+08:00
draft: false
description: "spring-boot-maven-plugin打包，使用Java并行流多线程发送kafka消息，刚开始发送时报错，Invalid value org.apache.kafka.common.serialization.StringSerializer for configuration key.serializer: Class org.apache.kafka.common.serialization.StringSerializer could not be found."
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Java", "spring-boot", "kafka"]
categories: ["Java", "问题实录"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/zh-cn/spring-boot-kafka-send-error-with-fork-join/"
---

spring-boot-maven-plugin打包，使用Java并行流多线程发送kafka消息，刚开始发送时报错，Invalid value org.apache.kafka.common.serialization.StringSerializer for configuration key.serializer: Class org.apache.kafka.common.serialization.StringSerializer could not be found.

<!--more-->

一、原因
类加载器不一样，如使用 spring-boot-maven-plugin 打包，业务处理发送kafka消息使用了 ForkJoin线程池，默认使用 SystemClassLoader，和 spring打包以后自定义的 ClassLoader不一样。

二、解决方案

1. 方案一：不使用 并行

2. 方案二：自定义线程池

注意：***建议使用 ForkJoinPool.submit() + join()。execute() 是 异步执行的，也就是说，这条消息 可能和 后面的消息同时处理，产生并发问题。***

```java
private ForkJoinPool bizPool = new ForkJoinPool(6, new ForkJoinWorkerThreadFactory() {
    @Override
    public ForkJoinWorkerThread newThread(ForkJoinPool pool) {
        return new ForkJoinWorkerThread(pool) {
        };
    }
}, null, false);

for (String msg : msgs) {
    bizPool.submit(() -> list.parallelStream().forEach(item -> {
        // do something, then send to kafka
    })).join();
}
```


三、参考链接

[kafka消费者报错：Class org.apache.kafka.common.serialization.StringDeserializer could not be found._Jaming R的博客-CSDN博客](https://blog.csdn.net/yixiaoqi2010/article/details/88987929)

[Kafka Producer - org.apache.kafka.common.serialization.StringSerializer could not be found - Stack Overflow](https://stackoverflow.com/questions/37363119/kafka-producer-org-apache-kafka-common-serialization-stringserializer-could-no)

[Fix StringSerializer could not be found when it not in ContextClassLoader by eshizhan · Pull Request #10938 · apache/kafka (github.com)](https://github.com/apache/kafka/pull/10938/files/a1d3e7ee2aa0d04b4a55e765eed7fdedf10dca23)
