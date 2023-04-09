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

<!--more-->

# 一、背景

- 公司业务分 2个Kafka，我们组一个，其他组公用一个
- 我们组有2个业务在 Java并行流中发消息到 其他组的Kafka，一个是 批量管理接口(app接口公用底层方法，不是批量的，没有用 并行流)，另一个是 消费我们组Kafka消息然后发送。
- 使用 spring-boot-maven-plugin 打包，发布到生产环境以后，偶尔会接到 发送消息到其他组Kafka报错告警，Invalid value org.apache.kafka.common.serialization.StringSerializer for configuration key.serializer: Class org.apache.kafka.common.serialization.StringSerializer could not be found.

# 二、临时方案

1. 查了 测试、开发 环境 最近1个月的日志，没有出现过这个错误
2. 网上搜索的结果，应该是 类加载器的问题
3. 本地 IDEA开发工具 启动程序、打包jar运行，访问 app接口，都没有重现
4. 生产环境第一次以后就正常，并且没有重现的情况下，不敢修改上线，只能先加异常处理

# 三、原因分析

- 类加载器不一样
- 使用 spring-boot-maven-plugin 打包出来是 fat jar，其中 BOOT-INF/lib/ 存放依赖jar，BOOT-INF/classes/ 存放项目的 classes，使用spring自定义的 ClassLoader 加载
- 业务处理使用了parallelStream包括发kafka消息，底层使用ForkJoin线程池，因为是JDK的类，使用BootClassLoader加载，BootClassLoader 加载不到 spring自定义目录 BOOT-INF的类

# 四、最终方案

1. 方案一：不使用 并行
接口这边批量不会特别大，并且是 操作Redis，就改回 普通stream

2. 方案二：自定义线程池
消费Kafka那边，原来加 parallelStream() 就是因为 每条消息要做 几个业务处理，串行的话，性能不够(Kafka分区数公司不允许加太多了，现在9个)

注意：***建议使用 自定义ForkJoinPool + submit() + join()。不能用 execute()，因为它是 异步执行的，也就是说，这条消息 可能和 后面的消息同时处理，产生并发问题。***

```java
// 自定义ForkJoinPool，默认的使用 BootClassLoader加载，有问题
ForkJoinPool bizPool = new ForkJoinPool(6, new ForkJoinWorkerThreadFactory() {
    @Override
    public ForkJoinWorkerThread newThread(ForkJoinPool pool) {
        return new ForkJoinWorkerThread(pool) {
        };
    }
}, null, false);
```

```java
for (String msg : msgs) {
    bizPool.submit(() -> list.parallelStream().forEach(item -> {
        // do something, then send to kafka
    })).join();
}
```

本文首发于 https://www.890808.xyz/spring-boot-kafka-send-error-with-fork-join/ ，其他平台需要审核更新慢一些。

![javalover123](https://img.890808.xyz/file/javalover123/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)

五、参考链接

[kafka消费者报错：Class org.apache.kafka.common.serialization.StringDeserializer could not be found._Jaming R的博客-CSDN博客](https://blog.csdn.net/yixiaoqi2010/article/details/88987929)

[Kafka Producer - org.apache.kafka.common.serialization.StringSerializer could not be found - Stack Overflow](https://stackoverflow.com/questions/37363119/kafka-producer-org-apache-kafka-common-serialization-stringserializer-could-no)

[Fix StringSerializer could not be found when it not in ContextClassLoader by eshizhan · Pull Request #10938 · apache/kafka (github.com)](https://github.com/apache/kafka/pull/10938/files/a1d3e7ee2aa0d04b4a55e765eed7fdedf10dca23)
