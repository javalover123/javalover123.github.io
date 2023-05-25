---
title: "多模块项目使用枚举配置spring-cache缓存"
date: 2023-05-25T22:05:22+08:00
draft: false
description: "1. 近期被刷接口了，考虑增加 本地缓存提高性能，另配置 限流；2. 使用 spring-cache 注解式缓存，可以提高使用缓存的开发效率；3. 不同业务，可以定制 自己的缓存策略，是基本需求；4. 多模块项目，最好在 统一的模块(如 common) 加载缓存配置"

tags: ["Java","Cache","缓存"]
categories: ["Java"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/multi-module-project-use-enum-config-spring-cache/"
---

<!--more-->

## 一、前言
1. 近期被刷接口了，考虑增加 本地缓存提高性能，另配置 限流
2. 使用 spring-cache 注解式缓存，可以提高使用缓存的开发效率
3. 不同业务，可以定制 自己的缓存策略，是基本需求
4. 多模块项目，最好在 统一的模块(如 common) 加载缓存配置

## 二、方案
### 1. 配置缓存：接口 + 枚举 + Lombok
缓存配置接口：
```java
public interface ICacheConfig {

    Integer getTtl();

}
```

common模块缓存配置(使用 Lombok 的 FieldNameConstants 自动生成 常量)：
```java
@lombok.Getter
@lombok.AllArgsConstructor
@lombok.experimental.FieldNameConstants(onlyExplicitlyIncluded = true)
public enum CommonCacheConfig implements ICacheConfig {

    @FieldNameConstants.Include QUOTE_LEVEL(1000, 2);

    private final Integer ttl;

}
```

业务模块缓存配置：
```java
@lombok.Getter
@lombok.AllArgsConstructor
@lombok.experimental.FieldNameConstants(onlyExplicitlyIncluded = true)
public enum QuoteServiceCacheConfig implements ICacheConfig {

    @FieldNameConstants.Include HOT_STOCK(1000, 30);

    private final Integer ttl;

}
```

### 2. 多模块配置加载：Reflections + SimpleCacheManager
- 通过 Reflections 库加载多模块配置
- SimpleCacheManager 组合 各种不同配置的 缓存
```java
@EnableCaching
@Configuration
public class CacheConfig {
    private Logger log = LoggerFactory.getLogger(this.getClass());
    @Bean
    @Primary
    public CacheManager cacheManager() {
        final SimpleCacheManager cacheManager = new SimpleCacheManager();

        final String prefix = "package";
```

```java
        Set<Class<? extends ICacheConfig>> classes = new Reflections(prefix).getSubTypesOf(ICacheConfig.class);
        log.info("cache types|{}|{}", prefix, classes);
        List<Cache> caches = classes.stream().flatMap(clazz -> Arrays.stream(clazz.getEnumConstants())).map(config -> {
            final Caffeine<Object, Object> cache = Caffeine.newBuilder().recordStats();
            Optional.ofNullable(config.getTtl()).ifPresent(t -> cache.expireAfterWrite(t, TimeUnit.SECONDS));
            return new CaffeineCache(((Enum) config).name(), cache.build());
        }).collect(Collectors.toList());
        cacheManager.setCaches(caches);
        return cacheManager;
    }
```

### 3. 使用缓存
- 使用 @Cacheable(cacheNames = CommonCacheConfig.Fields.QUOTE_LEVEL, sync = true)  操作缓存
- 使用 Lombok 的 FieldNameConstants 自动生成的 常量：
```java
public enum CommonCacheConfig implements ICacheConfig {

    public static final class Fields {
        public static final String QUOTE_LEVEL = "QUOTE_LEVEL";
    }

}
```

## 三、总结
- 通过 接口 + 枚举，业务模块不用改common模块， 新增枚举 就能 方便的配置、使用缓存，符合 开闭原则
- 通过 Lombok 的 FieldNameConstants 自动生成 枚举名称常量，便于代码 导航、重构
- 通过 Reflections 库，common模块自动加载 各模块的缓存配置，SimpleCacheManager 组合 各种不同配置的 缓存(CaffeineCacheManager 不能)，降低使用成本，提高可维护性
- sync = true，加锁，只有一个线程去加载数据，其他线程阻塞，防止 缓存击穿
- [alibaba/jetcache](https://github.com/alibaba/jetcache/blob/master/introduce_CN.md)：支持TTL和两级缓存、自动刷新和加载保护 等
- [netease-im/camellia](https://github.com/netease-im/camellia/blob/master/docs/cache/cache.md)：网易开源，有意思的是  支持基于注解执行mget，mevict等批量操作

本文首先发布于 [https://www.890808.xyz/](https://www.890808.xyz/) ，其他平台需要审核更新慢一些。

![javalover123](https://img.890808.xyz/file/javalover123/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)
