---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: APNs推送
platform: iOS
title: iOS正式环境推送收不到
root_cause: 正式包使用了开发环境的证书名(apns_dev)，而非正式环境证书
solution: 检查正式包的证书配置，确保使用正式环境证书名上报apns token
customers: ['万象森森']
source: chat_history
tags: ['iOS', 'APNs', '正式环境', '证书配置', 'apns_dev']
created: 2025-02-08
updated: 2026-03-23
---

## 问题：iOS iOS正式环境推送收不到

## 问题详情

**现象**：
iOS正式环境推送收不到，开发环境可以收到，怀疑证书配置问题

**环境信息**：
- 平台：iOS
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈iOS正式环境推送收不到
2. 查询accid: ua_858soqvmf37k
3. 发现该accid只有apns_dev的证书上报过apns token
4. 确认正式包使用了错误的证书名

## 问题原因

正式包使用了开发环境的证书名(apns_dev)，而非正式环境证书

## 解决方案

检查正式包的证书配置，确保使用正式环境证书名上报apns token

## 其他触发场景

（合并时在此处追加：`- [iOS] iOS正式环境推送收不到，来源：['万象森森']，2026-03-23`）
