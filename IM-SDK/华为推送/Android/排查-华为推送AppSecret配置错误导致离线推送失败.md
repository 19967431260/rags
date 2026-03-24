---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 华为推送
platform: Android
title: 华为推送AppSecret配置错误导致离线推送失败
root_cause: 控制台创建华为证书时AppSecret填写错误，使用了项目级而非应用级的AppSecret
solution: 在控制台创建华为证书时，使用应用级别的AppSecret，而非项目级别的
customers: ['万象森森']
source: chat_history
tags: ['华为推送', 'AppSecret', 'getAccessTokenNull', '离线推送']
created: 2025-02-07
updated: 2026-03-23
---

## 问题：Android 华为推送AppSecret配置错误导致离线推送失败

## 问题详情

**现象**：
华为推送token已上传但无离线推送，控制台创建华为证书时AppSecret填写错误

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈华为推送token已上传但无离线推送
2. 检查token: IQAAAACy1DKnAADSOqxBZYk_OORFIk1zxXtorU6pQ4micVrADEja_2_1CEfABtDJEwo-3T6zZKb1GzshB60M1iQnKiDDxCEIMiYDEm7IjF5XRG8kjg
3. 服务器报错: getAccessTokenNull|{"sub_error":20003,"error_description":"parameter invalid","error":1101}
4. 发现是AppSecret填错，应该填应用级别的而非项目级别的

## 问题原因

控制台创建华为证书时AppSecret填写错误，使用了项目级而非应用级的AppSecret

## 解决方案

在控制台创建华为证书时，使用应用级别的AppSecret，而非项目级别的

## 其他触发场景

（合并时在此处追加：`- [Android] 华为推送AppSecret配置错误导致离线推送失败，来源：['万象森森']，2026-03-23`）
