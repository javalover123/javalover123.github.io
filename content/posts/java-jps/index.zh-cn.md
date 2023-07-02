---
title: "Java程序性能分析：开篇之jps"
date: 2023-07-02T11:05:22+08:00
draft: false
description: "开发Java项目过程中，难免会碰到一些 性能 问题，这时候就需要一些工具，帮忙排查。本文开篇主要介绍 JDK自带的工具 jps，获取 Java程序列表，后面将继续介绍 JDK自带、第三方的 性能分析工具，敬请期待哦"

tags: ["Java","性能"]
categories: ["Java","性能"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/java-jps/"
---

<!--more-->

## 一、前言
- 开发Java项目过程中，难免会碰到一些 性能 问题，这时候就需要一些工具，帮忙排查
- 本文主要介绍 JDK自带的工具 jps，获取 Java程序列表，以 openjdk 11.0.10 为例

## 二、Java程序列表：jps
### 1. 简介
- 用来查找当前用户的 Java 进程，***而不能查找当前系统中其他用户的进程***
- 相比 `Linux系统` 的 ps -ef | grep java，`Windows系统`的 tasklist | findstr java，`jps` 查找Java进程命令更简洁
- ***列表里面会多一个 Jps的进程，每次进程号都不一样***  
![jps.png](https://img.890808.xyz/file/javalover123/2023/07/jps.png)

### 2. jps：输出 进程号、应用主类名
不包含包名，有些类名不容易分辨是哪个服务的进程，如下第3个 Launcher
```
15056 
31504 RemoteMavenServer36
17604 Launcher
11368 
32764 Jps
```

### 3. jps -l：输出 进程号、完全包名.应用主类名
输出包名，能帮助分辨 是哪个服务的进程，如下第3个是 IDEA开发工具的 Launcher
```
15056 
31504 org.jetbrains.idea.maven.server.RemoteMavenServer36
17604 org.jetbrains.jps.cmdline.Launcher
32324 jdk.jcmd/sun.tools.jps.Jps
11368
```

### 4. jps -m：多输出 jar 路径
相比 jps，多输出 jar 路径
![jps-m.png](https://img.890808.xyz/file/javalover123/2023/07/jps-m.png)

### 5. jps -v：多输出 启动参数
相比 jps，多输出 启动参数
![jps-v.png](https://img.890808.xyz/file/javalover123/2023/07/jps-v.png)

### 6. jps -V：输出通过 flag 文件传递到 JVM 中的参数(很少用到)
.hotspotrc 文件或 - XX:Flags = 所指定的文件。没有配置时，效果和 jps 一样

### 7. jps -q：只输出 进程号
- 只输出 进程号，比较适用于 docker、k8s容器等 只有1个Java进程的场景
- 但是还有一个 jps进程号干扰，并且只有进程号，不好区分哪个是 jps进程
```
15056
31504
17604
11368
```

## 三、总结
- 相比 `Linux系统` 的 ps -ef | grep java，`Windows系统`的 tasklist | findstr java，`jps` 查找Java进程命令更简洁
- 后面将继续介绍 JDK自带、第三方的 性能分析工具，敬请期待哦

**本文遵守[【CC BY-NC】协议，转载请保留原文出处及本版权声明，否则将追究法律责任。](https://creativecommons.org/licenses/by-nc/4.0/)**   
***本文首先发布于 [https://www.890808.xyz/](https://www.890808.xyz/) ，其他平台需要审核更新慢一些。***

![javalover123](https://img.890808.xyz/file/javalover123/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)