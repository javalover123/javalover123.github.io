---
title: "怎么把Java枚举名称作为注解的属性值"
date: 2023-05-20T22:05:22+08:00
draft: false
description: "Java注解的属性值，必须为 常量。有些场景想把 枚举名称 设置为 注解的属性值(如 spring-cache 用枚举配置缓存，使用时 需要 缓存名称)"

tags: ["Java"]
categories: ["Java"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/java-annotation-value-use-enum-name/"
---

<!--more-->

## 一、前言
- Java注解的属性值，必须为 常量
- 有些场景想把 枚举名称 设置为 注解的属性值(如 spring-cache 用枚举配置缓存，使用时 需要 缓存名称)

## 二、方案
### 方案一：名称属性 + 外部名称接口
```java
@lombok.Getter
@lombok.AllArgsConstructor
public enum CommonCacheConfig {
    QUOTE_LEVEL(CommonCacheConstant.QUOTE_LEVEL, 2);

    private final String name;

    private final int ttl;
}
```

```java
public interface CommonCacheConstant {

    String QUOTE_LEVEL = "QUOTE_LEVEL";

}
```
使用：@Cacheable(cacheNames = CommonCacheConstant.QUOTE_LEVEL)

### 方案二：名称属性 + 内部名称接口
```java
public enum CommonCacheConfig {
    QUOTE_LEVEL(Constant.QUOTE_LEVEL, 2);

    private final String name;
    private final Integer ttl;

    public interface Constant {
        String QUOTE_LEVEL = "QUOTE_LEVEL";
    }
}
```
使用：@Cacheable(cacheNames = CommonCacheConfig.Constant.QUOTE_LEVEL)

### 方案三：Lombok 的 FieldNameConstants
```java
@lombok.Getter
@lombok.AllArgsConstructor
@lombok.experimental.FieldNameConstants(onlyExplicitlyIncluded = true)
public enum CommonCacheConfig {

	@FieldNameConstants.Include QUOTE_LEVEL(2);

	private final Integer ttl;

}
```
使用：@Cacheable(cacheNames = CommonCacheConfig.Fields.QUOTE_LEVEL)  
注意：FieldNameConstants 的 onlyExplicitlyIncluded 需设置为 true，否则 按枚举的属性(如 ttl)生成，同时在 枚举项前加 @FieldNameConstants.Include

## 三、总结
- 通过 Lombok 的 FieldNameConstants 自动生成 枚举名称常量，提高了 可维护性
- 参考：[java - Use Enum type as a value parameter for @RolesAllowed-Annotation - Stack Overflow](https://stackoverflow.com/questions/3271659/use-enum-type-as-a-value-parameter-for-rolesallowed-annotation/45800305#45800305)

本文首先发布于 [https://www.890808.xyz/](https://www.890808.xyz/) ，其他平台需要审核更新慢一些。

![javalover123](https://img.890808.xyz/file/javalover123/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)
