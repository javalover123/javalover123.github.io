---
title: "Java代码性能测试实战之ContiPerf"
date: 2023-06-11T22:05:22+08:00
draft: false
description: "最近测试一个开源项目，发现生成的 全局id 有重复，方法加上 synchronized 提交PR后，有些同行对性能有疑虑，就准备做个 代码性能测试。Java基准性能测试 一般用 JMH 比较多，但是 官方建议 性能测试单独一个项目，感觉麻烦了点。发现 ContiPerf 可以方便的设置 执行次数、时长、线程数、预热时长，还有 Html格式报告，感觉还比较适合，基于 Junit"

tags: ["Java","test","单元测试","性能"]
categories: ["Java"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/java-performance-test-use-contiperf-base-junit/"
---

<!--more-->

## 一、前言
- 最近测试一个开源项目，发现生成的 `全局id` 有重复，方法加上 synchronized 提交PR后，有些同行对性能有疑虑，就准备做个 代码性能测试
- Java基准性能测试 一般用 [JMH](https://github.com/openjdk/jmh) 比较多，但是 官方建议 性能测试单独一个项目，感觉麻烦了点
- 后面发现了 [ContiPerf](https://github.com/javatlacati/contiperf/)，可以方便的设置 执行次数、时长、线程数、预热时长，还有 Html格式报告，感觉还比较适合，基于 Junit

## 二、[ContiPerf](https://github.com/javatlacati/contiperf/)
### 1. 安装
- 有2个仓库，这里选择 javatlacati 二开以后的
- 选择 2.4.3 版本，基于 Junit4，更好的支持 @After
- 另最新 2.4.4-SNAPSHOT 版本，基于Junit5
```xml
    <dependencies>
        <!-- 引入 ContiPerf 测试工具，参考 https://gitee.com/yu120/sequence -->
        <dependency>
            <groupId>com.github.javatlacati</groupId>
            <artifactId>contiperf</artifactId>
            <version>2.4.3</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
```

### 2. 使用
- 首先，单元测试类 增加属性 ContiPerfRule
- 测试方法增加 Junit4 的 @Test 注解
- 增加 @PerfTest，配置 invocations 次数，或 duration 毫秒时长，threads 线程数
- 性能测试嘛，最好配置 预热时长 warmUp，单位也是 毫秒
- 多种不同线程数的测试，可以 多个方法加 @PerfTest 注解哦(这种情况建议把 线程数加到 测试方法名末尾，线程数小于 10的 补0，同时测试类增加 @FixMethodOrder(MethodSorters.NAME_ASCENDING)，生成的 报告就按 线程数排序了)
- 还可以配置 @Required 结果校验哦，如下示例：每秒吞吐量要 大于等于 100万
```java
    @org.junit.Rule
    public ContiPerfRule contiPerfRule = new ContiPerfRule();

    @org.junit.Test
    @com.github.javatlacati.contiperf.Required(throughput = 100_0000)
    @PerfTest(duration = 3300, threads = 4, warmUp = 300)
    public void generateId04Threads() {
        generateIdThreads();
    }
```

### 3. 性能测试效果
- 所有的 PerfTest 结果都输出到 target/contiperf-report/index.html
![ContiPerf.png](https://img.890808.xyz/2023/06/f5eab981d4d05ad0f01a824f55dc8cc4.png)

### 4. 示例2：多线程生成id，有无重复校验
- ids 要使用 支持并发的容器，不然多线程 会报错
- @AfterClass 做结果校验
```java
    private static final Set<Long> ids = new ConcurrentHashSet<>((int) (INVOCATIONS / 0.7));
    @AfterClass
    public static void tearDown() {
        Assert.assertEquals("generateId duplicated", INVOCATIONS, ids.size());
    }

    @Test @PerfTest(invocations = INVOCATIONS, threads = 4)
    public void generateId() {
        ids.add(UniqueIdGenerator.generateId());
    }
```


## 三、总结
- [ContiPerf](https://github.com/javatlacati/contiperf/)，可以方便的设置 执行次数、时长、线程数、预热时长，还有 Html格式报告，是个比较便捷的 代码性能测试工具
- 更专业的 Java 微基准性能测试，也可以考虑 [JMH](https://github.com/openjdk/jmh) 哦

**本文遵守[【CC BY-NC】协议，转载请保留原文出处及本版权声明，否则将追究法律责任。](https://creativecommons.org/licenses/by-nc/4.0/)**   
***本文首先发布于 [https://www.890808.xyz/](https://www.890808.xyz/) ，其他平台需要审核更新慢一些。***

![javalover123](https://img.890808.xyz/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)