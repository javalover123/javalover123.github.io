---
title: "轻量级分布式日志追踪-Tlog快速入门"
date: 2023-06-06T22:05:22+08:00
draft: false
description: "公司目前还没有上 SkyWalking、Pinpoint等分布式追踪系统，所以先用个轻量级的吧。Tlog 只生成TraceId写入日志文件，没有 收集、存储、查询，所以 轻量"

tags: ["Java","log","分布式","日志"]
categories: ["Java"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/lightweight-distributed-log-tracker-tlog/"
---

<!--more-->

## 一、前言
- 公司目前还没有上 SkyWalking、Pinpoint等分布式追踪系统，所以先用个轻量级的吧
- [Tlog](https://gitee.com/dromara/TLog)：只生成TraceId写入日志文件，没有 收集、存储、查询，所以 轻量
- 以 spring-boot 2.3.12(非native) + log4j2 为例

## 二、快速入门
### 1. [选择接入方式](https://tlog.yomahub.com/pages/9c24c3/)
- 日志框架适配器方式 最稳定，优先选择
- [另有 Javaagent方式、字节码注入方式](https://tlog.yomahub.com/pages/9c24c3/)

### 2. 安装
- ***建议把 tlog的依赖 放到 log4j2前面，可以少修改 log4j2配置文件***
- 原项目依赖 hutool 时，版本不一致可能包冲突
- [全量依赖](https://tlog.yomahub.com/pages/977ce0/)
```xml
        <dependency>
            <groupId>com.yomahub</groupId>
            <artifactId>tlog-all-spring-boot-starter</artifactId>
            <version>1.5.0</version>
        </dependency>
```

- [按需依赖](https://tlog.yomahub.com/pages/9bca79/)
```xml
        <dependency>
            <groupId>com.yomahub</groupId>
            <artifactId>tlog-feign-spring-boot-starter</artifactId>
            <version>1.5.0</version>
        </dependency>
        <dependency>
            <groupId>com.yomahub</groupId>
            <artifactId>tlog-web-spring-boot-starter</artifactId>
            <version>1.5.0</version>
        </dependency>
```

### 3. [Log4j2框架适配器](https://tlog.yomahub.com/pages/8d5538/)
- 如果 tlog的依赖 没有放到 log4j2前面，需把pattern中的 m/msg/message 改成 tm/tmsg/tmessage
- 日志pattern 没有包含 %X 变量(MDC变量)时，可以不用增加 %TX{tl}，会自动记录
- ***日志pattern 包含 %X 变量时，需修改 pattern，增加 %TX{tl}，记录TraceId。否则不会记录TraceId***

### 4. 效果
启动日志：Converter key 'message' is already mapped to 'class com.yomahub.tlog.core.enhance.log4j2.AspectLogLog4j2Converter'
```txt
2020-09-16 18:12:56,748 [WARN] [TLOG]重新生成traceId[7161457983341056]  >> com.yomahub.tlog.web.TLogWebInterceptor:39
2020-09-16 18:12:56,763 [INFO] <0><7161457983341056> logback-dubbox-consumer:invoke method sayHello,name=jack  >> com.yomahub.tlog.example.dubbox.controller.DemoController:22
2020-09-16 18:12:56,763 [INFO] <0><7161457983341056> 测试日志aaaa  >> com.yomahub.tlog.example.dubbox.controller.DemoController:23
2020-09-16 18:12:56,763 [INFO] <0><7161457983341056> 测试日志bbbb  >> com.yomahub.tlog.example.dubbox.controller.DemoController:24
```

## 三、配置
### 1. [日志标签模板自定义](https://tlog.yomahub.com/pages/239d32/)
TLog默认只打出spanId和traceId，可修改 spring-boot 配置文件调整：
```
tlog.pattern=[$preApp][$preIp][$spanId][$traceId]
```

### 2. [自动打印调用参数和时间](https://tlog.yomahub.com/pages/250a98/)
默认不打印 参数和时间，可修改 spring-boot 配置文件调整：
```
tlog.enable-invoke-time-print=true
```

效果如下，方法开头增加 一行记录参数日志，末尾增加 耗时日志：
```txt
2020-12-01 19:20:07.768 [DubboServerHandler-127.0.0.1:30900-thread-2] INFO  c.y.tlog.dubbo.filter.TLogDubboInvokeTimeFilter - <0.1><7592057736843136> [TLOG]开始调用接口[DemoService]的方法[sayHello],参数为:["jack"]
2020-12-01 19:20:07.787 [DubboServerHandler-127.0.0.1:30900-thread-2] INFO  c.y.t.example.dubbo.service.impl.DemoServiceImpl - <0.1><7592057736843136> logback-dubbox-provider:invoke method sayHello,name=jack
2020-12-01 19:20:07.788 [Thread-14] INFO  c.y.tlog.example.dubbo.service.impl.AsynDomain - <0.1><7592057736843136> 这是异步方法哦
2020-12-01 19:20:07.788 [Thread-14] INFO  c.y.tlog.example.dubbo.service.impl.AsynDomain - <0.1><7592057736843136> 异步方法开始
2020-12-01 19:20:07.789 [Thread-14] INFO  c.y.tlog.example.dubbo.service.impl.AsynDomain - <0.1><7592057736843136> 异步方法结束
2020-12-01 19:20:07.795 [DubboServerHandler-127.0.0.1:30900-thread-2] INFO  c.y.tlog.dubbo.filter.TLogDubboInvokeTimeFilter - <0.1><7592057736843136> [TLOG]结束接口[DemoService]中方法[sayHello]的调用,耗时为:90毫秒
```

### 3. 错误处理
- but cannot be delegated to target bean. Switch its visibility to package or protected.
定时任务方法 不能是 private，需改为 package 或 protected

## 四、总结
- Tlog 适合中小型企业以及想快速解决日志追踪问题的公司项目使用
- 想知道 为什么pattern 包含 %X 变量时，不增加 %TX{tl} 就不记录 TraceId吗，留言 我再写一篇

本文首先发布于 [https://www.890808.xyz/](https://www.890808.xyz/) ，其他平台需要审核更新慢一些。

![javalover123](https://img.890808.xyz/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)