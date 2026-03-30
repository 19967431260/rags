---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 服务端API
platform: 服务端
title: Java调用新域名API证书不匹配错误
root_cause: JDK和httpclient版本较旧，不支持新域名的SNI证书。客户环境JDK 1.8.0_441与httpclient 4.4/5.3.1存在兼容性问题
solution: 使用临时域名api-hz-tmp.netease.im，或升级JDK到1.8.0_202及以上版本并配合兼容的httpclient版本
customers: ["北京中科大洋"]
source: chat_history
tags: ["Java", "SSL", "证书", "SNI", "JDK", "httpclient", "新域名"]
created: 2025-05-20
updated: 2025-03-20
---

## 问题：服务端 Java调用新域名API证书不匹配错误

## 问题详情

**现象**：
更换域名后调用云信API出现证书错误：Certificate for <api.yunxinapi.com> doesn't match any of the subject alternative names: [*.netease.im, netease.im]。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：服务端

## 排查过程

1. 检查网络 → dig查看IP
2. 检查JDK版本 → 1.8 httpclient 4.4
3. 获取详细堆栈 → 发现SSLException
4. 尝试升级JDK → 1.8.0_441出现NoClassDefFoundError
5. 尝试升级httpclient → 5.3.1出现SecurityException
6. 提供临时域名 → 使用api-hz-tmp.netease.im

## 问题原因

JDK和httpclient版本较旧，不支持新域名的SNI证书。客户环境JDK 1.8.0_441与httpclient 4.4/5.3.1存在兼容性问题

## 解决方案

使用临时域名api-hz-tmp.netease.im，或升级JDK到1.8.0_202及以上版本并配合兼容的httpclient版本

## 其他触发场景

