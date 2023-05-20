---
title: "Java annotation value use enum name"
date: 2023-05-20T22:05:22+08:00
draft: false
description: "Java annotation value must be constant, but some case want to use enum name(eg. spring-cache use enum config cache, operate cache need cache name)"

tags: ["Java"]
categories: ["Java"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/en/java-annotation-value-use-enum-name/"
---

<!--more-->

## 1. Background
- Java annotation value must be constant
- But some case want to use enum name(eg. spring-cache use enum config cache, operate cache need cache name)

## 2. Plan
- Plan 1: name property + external name interface
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
Usage：@Cacheable(cacheNames = CommonCacheConstant.QUOTE_LEVEL)

- Plan 2: name property + internal name interface
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
Usage：@Cacheable(cacheNames = CommonCacheConfig.Constant.QUOTE_LEVEL)

- Plan 3：Lombok's FieldNameConstants
```java
@lombok.Getter
@lombok.AllArgsConstructor
@lombok.experimental.FieldNameConstants(onlyExplicitlyIncluded = true)
public enum CommonCacheConfig {

	@FieldNameConstants.Include QUOTE_LEVEL(2);

	private final Integer ttl;

}
```
Usage：@Cacheable(cacheNames = CommonCacheConfig.Fields.QUOTE_LEVEL)  
Attention: FieldNameConstants's onlyExplicitlyIncluded must set to true，otherwise generate by property(eg. ttl), and add @FieldNameConstants.Include before enum item.

## 3. Summary
- Use Lombok's FieldNameConstants auto generate enum name constant, improved maintainability
- Refer：[java - Use Enum type as a value parameter for @RolesAllowed-Annotation - Stack Overflow](https://stackoverflow.com/questions/3271659/use-enum-type-as-a-value-parameter-for-rolesallowed-annotation/45800305#45800305)

The post first published at [https://www.890808.xyz/](https://www.890808.xyz/) ，others update slowly.

![javalover123](https://img.890808.xyz/file/javalover123/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)
