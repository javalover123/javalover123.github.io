---
title: "开源Java诊断工具Arthas：开篇之watch实战"
date: 2023-08-16T22:05:22+08:00
draft: false
description: "Java项目中，测试环境 难免会碰到一些问题，这时候就需要一些工具，帮忙排查。本文开篇主要介绍 阿里开源的诊断工具Arthas 3.7.0版本，watch、jad、classloader 命令，以 Debian 11、openjdk 11 为例。后面将继续介绍 Arthas 的其他妙用，敬请期待哦"

tags: ["Java","性能","arthas"]
categories: ["Java","性能","arthas"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/java-arthas-watch-jad"
---

<!--more-->

## 一、前言  
- 还在为排查Java程序线上问题头痛吗，看我们用阿里开源的诊断神器 Arthas 来帮您
- 本文开篇主要介绍 阿里开源的诊断神器Arthas 3.7.0版本，watch、jad、classloader 命令，以 Debian 11、openjdk 11 为例

## 二、Arthas 简介和安装  
### 1. [简介](https://arthas.aliyun.com/doc/)  
- Arthas 是一款线上监控诊断产品，通过全局视角实时查看应用 load、内存、gc、线程的状态信息
- 并能在不修改应用代码的情况下，对业务问题进行诊断，包括查看方法调用的出入参、异常
- 监测方法执行耗时，类加载信息等，大大提升线上问题排查效率。

### 2. [安装和启动](https://arthas.aliyun.com/doc/install-detail.html)  
- **执行该程序的用户需要和目标进程具有相同的权限，最好和目标进程的用户一致**
- 启动以后，输入 数字 选择要观察的进程，也可增加` --select jar名称` **自动选择进程，提高操作效率**
- 还可以在 **末尾增加 进程号(启动后也不用选择进程了)**  
```shell
curl -O https://arthas.aliyun.com/arthas-boot.jar && java -jar arthas-boot.jar
```

## 三、watch命令  
### 1. [基本用法](https://arthas.aliyun.com/doc/watch.html)  
- 观察指定函数的调用情况，如 入参、返回值、抛出异常，通过编写 OGNL 表达式查看
- 命令格式：`watch 类全名或类名表达式 函数名表达式 {观察表达式} -x 输出深度 -n 次数`
- 观察表达式：默认 {params, target, returnObj}，分别是 参数列表、被观察对象、返回值
- `-x 输出深度`：默认为 1，最大为 4。默认的 观察表达式中 params + 输出深度 1，只能输出 params 是否 empty，size 是 几，要看到内容就要加大 输出深度 或 改为 `params[0]`
- 很多时候，我们都不关注 被观察对象 target，指定 观察表达式 可以降低干扰，尤其是 属性多 或 输出深度大的时候
- **观察执行频繁的方法，最好指定 -n 次数，避免刷屏**  
![arthas-watch.png](https://img.890808.xyz/2023/08/arthas-watch.png)

### 2. [只想看满足条件的](https://arthas.aliyun.com/doc/watch.html#%E6%9D%A1%E4%BB%B6%E8%A1%A8%E8%BE%BE%E5%BC%8F%E7%9A%84%E4%BE%8B%E5%AD%90)  
- 如 测试环境 同时有其他人访问，只想看到自己的请求
- 命令格式：`watch 类全名或类名表达式 函数名表达式 {观察表达式} '条件' -x 输出深度 -n 次数`  
![arthas-watch-condition.png](https://img.890808.xyz/2023/08/arthas-watch-condition.png)

### 3. [只想看耗时长的](https://arthas.aliyun.com/doc/watch.html#%E6%8C%89%E7%85%A7%E8%80%97%E6%97%B6%E8%BF%9B%E8%A1%8C%E8%BF%87%E6%BB%A4)  
- 命令格式：条件 替换为 `#cost>毫秒数`  
![arthas-watch-cost.png](https://img.890808.xyz/2023/08/arthas-watch-cost.png)

### 4. 重载方法
- 重载方法，可通过参数 个数、类型 筛选
- 命令格式：`watch 类全名或类名表达式 函数名表达式 {观察表达式} 'params.length== 参数个数 && params[0] instanceof java.lang.String`  
![arthas-watch-overload.png](https://img.890808.xyz/2023/08/arthas-watch-overload.png)

### 5. 实现类 和 代理类 输出2次  
- 增加参数，非代理类才输出：` --exclude-class-pattern *Enhance*`  
- 不匹配子类：`options disable-sub-class true`  
![arthas-watch-proxy.png](https://img.890808.xyz/2023/08/arthas-watch-proxy.png)

### 6. 匹配类数量超限(默认50个)  
- 错误信息：The number of matched classes is 1501, greater than the limit value 50
- 增加参数 ` -m 数量`，指定 Class 最大匹配数量，默认值为 50，注意值小于实际类匹配数时报错，也就是说 只能大于等于 类匹配数
- 类名表达式 包含 `*` 导致匹配类太多的，建议把 类名表达式 写的更精确
- 子类太多：试试用 子类全名 + 方法，或 不匹配子类：`options disable-sub-class true`，或 提高匹配类数量 ` -m 2000`  
![arthas-watch-maxMatch.png](https://img.890808.xyz/2023/08/arthas-watch-maxMatch.png)

### 7. 观察异常  
- 4 个观察事件点，即 -b 函数调用前，-e 函数异常后，-s 函数返回后，-f 函数结束后(默认)
- 命令格式：`watch 类全名或类名表达式 函数名表达式 {throwExp} -e`  
![arthas-watch-exception.png](https://img.890808.xyz/2023/08/arthas-watch-exception.png)

### 8. 观察函数调用前的入参  
- 这种情况比较少，一般是 入参、出参 是同一个 集合 或 对象，方法中修改了 内容
- 命令格式：`watch 类全名或类名表达式 函数名表达式 {观察表达式} -b`，观察表达式 中 returnObj 是 null 哦，因为还没执行完返回  

## 四、拓展  
### 1. 怀疑代码不一致，[jad 反编译 确认一下吧](https://arthas.aliyun.com/doc/jad.html)  
- 命令格式：jad 类全名或类名表达式 函数名表达式，方法名 是 可选的(**代码行数多的类建议加 方法名，避免刷屏**)，不传就反编译整个类  
- 只显示源代码，不显示 ClassLoader、Location：` --source-only `  
- 不显示行号：` --lineNumber false `  
![arthas-jad.png](https://img.890808.xyz/2023/08/arthas-jad.png)

### 2. 啥，jad 找不到类  
- 有一次，发版发了几次都看不到效果，原来是 发错服务了，囧，谁让服务名称前缀是一样的呢，只能怪自己了
- 手动要加载也是可以的，[classloader | arthas (aliyun.com)](https://arthas.aliyun.com/doc/classloader.html#%E4%BD%BF%E7%94%A8-classloader-%E5%8E%BB%E5%8A%A0%E8%BD%BD%E7%B1%BB)，需指定 classLoader，如下示例
- `classloader --classLoaderClass org.springframework.boot.loader.LaunchedURLClassLoader --load java.lang.String`  
![arthas-classloader-load.png](https://img.890808.xyz/2023/08/arthas-classloader-load.png)

## 五、总结  
- Arthas 可以帮我们诊断不少线上问题，如 查看方法调用的出入参、异常，监测方法执行耗时，类加载信息等，大大提升线上问题排查效率。
- [FAQ | arthas (aliyun.com)](https://arthas.aliyun.com/doc/faq.html)
- 后记：想当年还用过 阿里大神开源的 [greys](https://github.com/oldmanpushcart/greys-anatomy)，一转眼用 Arthas 也几年了，而 Arthas 也是基于 greys 开发的

**本文遵守[【CC BY-NC】协议，转载请保留原文出处及本版权声明，否则将追究法律责任。](https://creativecommons.org/licenses/by-nc/4.0/)**   
***本文首先发布于 [https://www.890808.xyz/](https://www.890808.xyz/) ，其他平台需要审核更新慢一些。***

![javalover123](https://img.890808.xyz/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)