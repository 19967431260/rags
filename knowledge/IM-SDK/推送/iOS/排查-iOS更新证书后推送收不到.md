---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 推送
platform: iOS
title: iOS更新证书后推送收不到
root_cause: 证书被吊销或配置问题导致推送失败
solution: 1. 确保证书名称与代码中初始化的apnscername一致
customers: ["青岛上啥班"]
source: chat_history
tags: ["iOS", "推送", "证书", "apnscername", "certificate_revoked"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：iOS更新证书后推送收不到

## 问题详情

**现象**：
客户更新云信证书后，聊天推送收不到。

**环境信息**：
- 平台：iOS

## 排查过程

1. 客户反馈更新证书后推送收不到
2. 询问是否更新了apnscername
3. 客户提供发送方和接收方accid
4. 查询推送日志发现SSLHandshakeException: certificate_revoked错误
5. 建议用第三方工具测试证书

## 根因分析

证书被吊销或配置问题导致推送失败

## 解决方案

1. 确保证书名称与代码中初始化的apnscername一致
2. 检查证书是否被吊销（certificate_revoked错误）
3. 使用第三方推送工具（如knuff）测试证书有效性
4. pushkit配置如不需要可以删除

## 其他触发场景

（无）
