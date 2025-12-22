---
title: "分享使用 Google Antigravity 账号不可用、2api 的实战经验"
date: 2025-12-22T22:05:22+08:00
draft: false
description: "分享使用 Google Antigravity 账号不可用、2api 的实战经验，如 网络配置、解决部分账号 this account is ineligible to use Antigravity、本地客户端 转api、服务器上 转api 等"

tags: ["AI", "人工智能", "大模型", "LLM", "Vibe Coding"]
categories: ["AI"]

lightgallery: true

repost:
  enable: true
  url: "https://www.890808.xyz/2025/use-google-antigravity-2api/"
---

<!--more-->

# 一、本地客户端使用
## 1. 前提：解决网络问题

* 建议全局 TUN模式(可选 系统代理)，或搭配 Proxifier(Windows可选 Netch)
* 详情参考 [谷歌IDE antigravity 解决登陆问题-- win、mac通用版本 - 开发调优 - LINUX DO](https://linux.do/t/topic/1190670)

## 2. 解决部分账号 this account is ineligible to use Antigravity
* [Antigravity-Manager](https://github.com/lbjlaq/Antigravity-Manager)
本人有个多年老账号，登录提示 this account is ineligible to use Antigravity，使用大佬开源的工具，成功登录获取到模型配额，添加2个或以上账号后，在 `账号管理` 页面，点击 右侧操作里面的第2个按钮 `切换到此账号`，我本地的 Antigravity 成功登录了。开启 `API 反代` 后，在 `Cherry Studio` 成功使用。同时支持 多账号管理、切换 哦，今年新注册的账号，也有一部分用该工具能获取到模型配额
* 详情参考 [「开源自荐」重构了一下 antigravity 切换账号工具 - 开发调优 - LINUX DO](https://linux.do/t/topic/1317411/1)

# 二、本地客户端 转api
## Antigravity-Manager
只测试了 [Antigravity-Manager](https://github.com/lbjlaq/Antigravity-Manager)，详情参考 上面第2点

# 三、服务器上 转api
## [deanxv/done-hub](https://github.com/deanxv/done-hub)
1. 优点
[Docker 镜像部署](https://github.com/su-kaka/gcli2api?tab=readme-ov-file#docker-%E7%8E%AF%E5%A2%83)简单，[文档提到了 远程部署时，用本地浏览器进行 OAuth授权 的解决方案](https://linux.do/t/topic/1342907)，授权成功后改域名端口然后回车。还有一点，2api后测试起来速度快(gemini-2.5-flash-lite 1.3秒左右)，稳定

2. 多账号支持
开启 批量添加，替换授权文件里面的换行，每行放一个授权文件内容。或者创建多个渠道，每个渠道一个账号

3. 详情参考 [【done-hub】已支持Antigravity渠道～小白也能看懂的Antigravity2API教程！ - 开发调优 - LINUX DO](https://linux.do/t/topic/1342907)

## [su-kaka/gcli2api](https://github.com/su-kaka/gcli2api)
自带多账号管理，但是可能我账号授权不到位或其他原因，2api后测试要 11秒左右，并且账号经常变 404

## 区别与联系
done-hub 接入 Antigravity 部分交互及代码参考[gcli2api](https://github.com/su-kaka/gcli2api)，感谢 gcli2api 的贡献。另外2个项目OAuth的格式有点区别，左边是 gcli2api、右边是 done-hub。
![done-hub 和 gcli2api 的 OAuth格式区别](https://linux.do/uploads/default/original/4X/d/6/8/d68cc82c722fa0f77b73151d772f08abc2cd9c05.png)


# 四、感谢各位佬友阅读，希望能有所帮助，方便的点个赞，谢谢！

---
本文首先发布于 [https://www.890808.xyz/](https://www.890808.xyz/) ，其他平台需要审核更新慢一些。

![javalover123](https://img.890808.xyz/2023/04/688b88cfd4ed9f6fcd56828b849ce47c.jpg)
