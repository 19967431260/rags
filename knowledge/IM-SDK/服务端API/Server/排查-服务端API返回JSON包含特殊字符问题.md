---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 服务端API
platform: Server
title: 服务端API返回JSON包含特殊字符问题
root_cause: 客户代码解析问题，postman测试返回正常，可能是客户使用的HTTP客户端或解析库存在问题
solution: 建议使用官方提供的服务端SDK：https://github.com/netease-im/yunxin-im-server-sdk/tree/main。如仍有问题，使用postman或curl测试并截图完整的请求和响应。
customers: ["深圳享笑"]
source: chat_history
tags: ["JSON", "特殊字符", "解析失败", "服务端API", "SDK"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：服务端API返回JSON包含特殊字符问题

## 问题详情

**现象**：
客户反馈从去年年底开始，服务端API返回的JSON中夹杂着特殊字符导致解析失败。

**环境信息**：
- 平台：服务端

## 排查过程

1. 客户反馈API返回的JSON包含异常字符
2. 客户提供的错误示例显示code值前插入了数字
3. 建议客户使用postman测试
4. 客户反馈postman测试正常
5. 建议客户使用官方服务端SDK

## 根因分析

客户代码解析问题，postman测试返回正常，可能是客户使用的HTTP客户端或解析库存在问题

## 解决方案

建议使用官方提供的服务端SDK：https://github.com/netease-im/yunxin-im-server-sdk/tree/main。如仍有问题，使用postman或curl测试并截图完整的请求和响应。

## 其他触发场景

（无）
