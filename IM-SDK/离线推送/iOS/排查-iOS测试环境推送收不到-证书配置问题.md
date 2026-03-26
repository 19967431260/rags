---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: iOS
title: iOS测试环境推送收不到：证书配置问题
root_cause: 测试环境appkey缺少appstorepub证书，客户端实际使用的证书名是appstorepub
solution: 在控制台为测试环境appkey补充appstorepub证书；客户端需同步使用相同证书名（dev和appstorepub）；证书名须在APP内和控制台完全对齐
customers: ["上海抱朴"]
source: chat_history
tags: ["iOS", "推送", "appstorepub证书", "测试环境", "离线推送"]
created: 2025-07-08
updated: 2025-07-25
---

## 问题：iOS 测试环境推送收不到：证书配置问题

## 问题详情

**现象**：
iOS测试环境收不到消息推送，APP内和控制台证书名已对齐但仍无法收到。

**复现步骤**：
1. iOS设备集成SDK
2. 测试环境发送消息
3. 设备无法收到离线推送通知

## 排查过程

1. 客户提供SDK日志进行排查
2. 确认APP内和控制台证书名已对齐，未发现配置错误
3. 进一步核查发现测试环境appkey没有配置appstorepub证书
4. 客户提供截图确认，发现客户端实际使用的证书名是appstorepub

**关键发现**：测试环境appkey缺少appstorepub证书，导致推送无法送达。

## 问题原因

测试环境appkey未配置appstorepub证书，而客户端使用了该证书名，导致APNs推送无法建立有效连接。

## 解决方案

1. 在云信控制台为测试环境appkey补充配置appstorepub证书
2. 客户端确保使用相同的证书名（dev和appstorepub）
3. 证书名须在APP内和控制台完全对齐
