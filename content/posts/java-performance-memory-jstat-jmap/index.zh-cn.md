---
title: "Java程序性能分析：内存"
date: 2023-07-09T11:05:22+08:00
draft: false
description: "开发Java项目过程中，难免会碰到一些 性能 问题，这时候就需要一些工具，帮忙排查。本文主要介绍 JDK自带的工具 jstat、jmap，另简单介绍 MAT、gceasy、HeapDump 等"

tags: ["Java","性能"]
categories: ["Java","性能"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/java-performance-memory-jstat-jmap/"
---

<!--more-->

## 一、前言
- 开发Java项目过程中，难免会碰到一些 性能 问题，这时候就需要一些工具，帮忙排查
- 本文主要介绍 JDK自带的工具 jstat、jmap，用于分析内存问题，另简单介绍 MAT、gceasy、HeapDump 等
- 以 openjdk 11.0.13、G1 垃圾收集器、Linux系统 为例

## 二、GC分析：jstat
### 1. [jstat 简介](https://docs.oracle.com/en/java/javase/11/tools/jstat.html)
- jstat 全称 “Java Virtual Machine statistics monitoring tool”，位于 JDK 的 bin 目录下，用于对 Java 程序的资源和性能进行监控，包括 Heap size、垃圾回收状况 等。
- jstat --help：查看命令帮助
- jstat -options：返回有哪些命令选项，如 -gcutil、-gc、-gccapacity、-gccause，另有 -class、-compiler、-printcompilation 等
- `jstat 上一步输出的命令选项 [-t] [-h每几行输出标题行] 进程号 [持续输出间隔时长 [输出次数]]`
- 持续输出间隔时长 默认毫秒，数字后面加 `s` 单位改为秒，`-t` 表示每行开头输出 相对应用启动时间的Timestamp 时间戳

### 2. jstat -gcutil
- 常用命令格式：jstat -gcutil 进程号 持续输出间隔毫秒数，下图每隔 1000毫秒输出一次
- 前6列 输出各个内存区域使用百分比 (没有容量大小)，依次是 幸存区survivor0、1、新生代Eden、老年代Old、元数据 Metaspace、Compressed class space
- GC 结尾的列 表示 GC次数，GCT 结尾的 表示 GC耗时，依次是 Young GC 次数和耗时、Full GC、Compressed class space GC，最后一列 GCT 是 Total总GC耗时
- 2次相邻的GC，可以快速判断那一次GC的耗时；GCT / GC = 平均每次GC耗时
- GC是否频繁标准参考：Young GC执行迅速(50毫秒以内)、Young GC执行不频繁(间隔10秒左右一次)、Full GC执行迅速(1秒以内)、Full GC执行不频繁(间隔10分钟左右一次)   
![jstat-gcutil.png](https://img.890808.xyz/file/javalover123/2023/07/jstat-gcutil.png)

### 3. jstat -gc
- 列出 各区域的容量Capacity、使用大小 Utilization，单位是 KB，***有容量大小，没有百分比***
- YGC 开始，是各区域 GC次数、耗时   
![jstat-gc.png](https://img.890808.xyz/file/javalover123/2023/07/jstat-gc.png)

### 4. jstat -gccapacity
- 主要关注 各区域 最小(Min，MN结尾)、最大(Max，MX结尾)、当前(Capacity，C结尾) 容量 capacity
- 最后3列 YGC、FGC、CGC 分别是 Young、Full、Compressed class space 区域 GC次数
- NGCMN 是 新生代最小容量 new generation capacity min
- 各个分区的容量，单位是 KB   
![jstat-gccapacity.png](https://img.890808.xyz/file/javalover123/2023/07/jstat-gccapacity.png)

## 三、内存分析：jmap
### 1. [jmap 简介](https://docs.oracle.com/en/java/javase/11/tools/jmap.html)
jmap 可以 快速分析简单的内存占用，生成 dump文件 便于后续分析

### 2. jmap -histo
- 快速检测明显的内存问题(看不出来问题，可以下一步 jmap -dump)
- 命令格式：jmap -histo 进程号，***建议后面加 ` | head -行数`，不然就等着刷屏吧***    
![jmap-histo.png](https://img.890808.xyz/file/javalover123/2023/07/jmap-histo.png)


### 3. jmap -dump
- 生成的文件，用于深层次分析内存问题
- 命令格式：`jmap -dump:format=b,file=heap.bin <pid>`
- GC以后再 dump，可以确定是不是还没有触发GC，内存占用才高，格式是在 `-dump:` 后面增加 `live,`
- dump文件如果在服务器，建议压缩以后在传输，如下图 文件大小降低70%
- 如果是在远程容器里面，下载到本地可能报错，压缩 + 重试 大概率能解决   
![jmap-dump.png](https://img.890808.xyz/file/javalover123/2023/07/jmap-dump.png)


## 四、其他内存分析工具
### 1. [MAT](https://www.eclipse.org/mat/)：免费经典的dump分析工具
- MAT 全称 Eclipse Memory Analysis Tools，是一个分析 Java 堆数据的专业工具，可以计算出内存中对象的实例数量、占用空间大小、引用关系等，看看是谁阻止了垃圾收集器的回收工作，从而定位内存泄漏的原因。
- 建议配置略大于 dump文件大小的内存，否则可能报错，编辑 MemoryAnalyzer.ini 添加 -vmargs – Xmx4g
### 2. [gceasy.io](https://gceasy.io/)：国外的在线分析工具
### 3. [HeapDump社区](https://memory.console.heapdump.cn/)
阿里大神创业的产品，除了工具，还有不少性能方面的案例

## 五、总结
- jstat 可以看到 容量、使用量、最小最大容量、使用率、GC耗时、GC是否频繁
- jmap 可以 快速分析简单的内存占用，生成 dump文件 便于后续分析
- 另罗列了 MAT、gceasy.io、HeapDump社区 等，鉴于篇幅原因，暂时不细说了

**本文遵守[【CC BY-NC】协议，转载请保留原文出处及本版权声明，否则将追究法律责任。](https://creativecommons.org/licenses/by-nc/4.0/)**   
***本文首先发布于 [https://www.890808.xyz/](https://www.890808.xyz/) ，其他平台需要审核更新慢一些。***

![javalover123](https://img.890808.xyz/file/javalover123/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)