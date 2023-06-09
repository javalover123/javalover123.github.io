---
title: "Testng和Junit5多线程并发测试实战"
date: 2023-06-08T22:05:22+08:00
draft: false
description: "最近测试一个开源项目，发现生成的 全局id 有重复，也没有单元测试，就准备贡献个 PR。想到多线程并发测试，根据经验，第一想法是用 Testng，后面看了下 Junit5也有实验性支持了，就对比下(以 maven 为例)"

tags: ["Java","test","单元测试"]
categories: ["Java"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/parallel-tests-using-testng-or-junit5/"
---

<!--more-->

## 一、前言
- 最近测试一个开源项目，发现生成的 `全局id` 有重复，也没有单元测试，就准备贡献个 `PR`
- 想到多线程并发测试，根据经验，第一想法是用 [Testng](https://github.com/testng-team/testng)，后面看了下 [Junit5](https://github.com/junit-team/junit5) 也有实验性支持了，就对比下(以 `maven` 为例)
- [spock](https://github.com/spockframework/spock) 不太适合这种场景

## 二、[Testng](https://testng.org/doc/documentation-main.html#parallel-tests)
### 1. 安装
- 选择 使用数 比较多、也比较新 的版本，7.7.1。<testng.version>7.7.1</testng.version>
- 多模块项目，可以在 根pom.xml里面添加依赖，避免每个模块都增加配置哦
```xml
    <dependencies>
        <!-- test -->
        <dependency>
            <groupId>org.junit.jupiter</groupId>
            <artifactId>junit-jupiter</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>
```

### 2. 使用
- [@Test 就可以指定 执行次数(invocationCount)、并发(threadPoolSize)，很方便](https://testng.org/doc/documentation-main.html#parallel-tests)
- 同一个测试对象，ids属性 不用加 static
```java
public class UniqueIdGeneratorTest {
    private Set<Long> ids = new ConcurrentHashSet<>(128);

    @org.testng.annotations.Test(invocationCount = 128, threadPoolSize = 3)
    public void testGenerateId() {
        final Long id = UniqueIdGenerator.generateId();
        assertTrue(ids.add(id), "id exists," + id);
    }

}
```

### 3. 效果
![testng.png](https://img.890808.xyz/file/javalover123/2023/06/2794bd5249788bc70c764d5ce2cdf152.png)

## 三、[Junit5](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parallel-execution)
### 1. 安装
- 选择 使用数 比较多、也比较新 的版本，5.8.2。<junit-jupiter.version>5.8.2</junit-jupiter.version>
- 最好通过 dependencyManagement 来统一版本，尤其是 多模块项目
- 建议放到 spring-boot-dependencies 前面，优先级更高
```xml
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.junit</groupId>
                <artifactId>junit-bom</artifactId>
                <version>${junit-jupiter.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>    </dependencyManagement>
```

多模块项目，可以在 根pom.xml里面添加依赖，避免每个模块都增加配置哦
```xml
    <dependencies>
        <!-- test -->
        <dependency>
            <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>${testng.version}</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
```

### 2 [配置项](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parallel-execution-config)
- ***先设置 junit.jupiter.execution.parallel.enabled=true***
- 全局并发测试：junit.jupiter.execution.parallel.mode.default=concurrent
- 局部并发测试：@RepeatedTest 和 @Execution(CONCURRENT)
- ***[按需配置并行策略 strategy](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parallel-execution-config)，建议 fixed，线程数 可控***
- [fixed 配置：如 fixed.parallelism=3，fixed.max-pool-size=3(默认 256 + parallelism)](https://github.com/junit-team/junit5/blob/f58cd419755846f1476e8d15783438de8d7aede4/junit-platform-engine/src/main/java/org/junit/platform/engine/support/hierarchical/DefaultParallelExecutionConfigurationStrategy.java#L44)
![junit5-fixed.png](https://img.890808.xyz/file/javalover123/2023/06/422bfec8970a12e6526e40dee50ebed5.png)

- [dynamic策略(根据 factor、CPU核数 调整parallelism)，parallelism = max(1, factor * CPU核数)，后面和 fixed 逻辑一样](https://github.com/junit-team/junit5/blob/f58cd419755846f1476e8d15783438de8d7aede4/junit-platform-engine/src/main/java/org/junit/platform/engine/support/hierarchical/DefaultParallelExecutionConfigurationStrategy.java#L67)
![junit5-dynamic.png](https://img.890808.xyz/file/javalover123/2023/06/edd7361ac51d4f17184847b2b152822b.png)

### 3 [配置方式](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parallel-execution-config)
- ***System properties 配置方式，更适合多模块项目(根pom.xml配置，子模块就不用配置了)***
```xml
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>2.18.1</version>
                <configuration>
                    <argLine>-Djunit.jupiter.execution.parallel.enabled=true -Djunit.jupiter.execution.parallel.config.strategy=fixed
                        -Djunit.jupiter.execution.parallel.config.fixed.parallelism=3 -Djunit.jupiter.execution.parallel.config.fixed.max-pool-size=3
                    </argLine>
                </configuration>
            </plugin>
```

- [配置文件](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parallel-execution-config)
test/resources 目录下，增加 junit-platform.properties 文件，内容如下：
```
#是否允许并行执行true/false
junit.jupiter.execution.parallel.enabled=true
#是否支持方法级别多线程same_thread/concurrent
junit.jupiter.execution.parallel.mode.default=concurrent
#是否支持类级别多线程same_thread/concurrent
junit.jupiter.execution.parallel.mode.classes.default=concurrent
# the maximum pool size can be configured using a ParallelExecutionConfigurationStrategy
junit.jupiter.execution.parallel.config.strategy=fixed
junit.jupiter.execution.parallel.config.fixed.parallelism=3
junit.jupiter.execution.parallel.config.fixed.max-pool-size=3
```

### 4. 使用
- [需改为 @RepeatedTest，和 普通测试不一致，并发线程数 是全局的](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parallel-execution)
- 测试对象 不同，ids属性 需加 static
```java
class UniqueIdGeneratorTest2 {
    private static Set<Long> ids = new ConcurrentHashSet<>(128);

    @org.junit.jupiter.api.RepeatedTest(128)
    @org.junit.jupiter.api.parallel.Execution(ExecutionMode.CONCURRENT)
    void generateId() {
        final Long id = UniqueIdGenerator.generateId();
        assertTrue(ids.add(id), "id exists," + id);
    }
}
```

### 5. 效果
![junit5.png](https://img.890808.xyz/file/javalover123/2023/06/a46900b7e5875b317a68d6798940f916.png)

## 四、总结
- 多线程并发测试 场景，[Testng](https://testng.org/doc/documentation-main.html#parallel-tests) 可能比 [Junit5](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parallel-execution) 更合适
- 使用不多也可以试试 [hutool 的 ThreadUtil#concurrencyTest(int threadSize, Runnable runnable)](https://gitee.com/dromara/hutool/)

**本文遵守[【CC BY-NC】协议，转载请保留原文出处及本版权声明，否则将追究法律责任。](https://creativecommons.org/licenses/by-nc/4.0/)**   
***本文首先发布于 [https://www.890808.xyz/](https://www.890808.xyz/) ，其他平台需要审核更新慢一些。***

![javalover123](https://img.890808.xyz/file/javalover123/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)