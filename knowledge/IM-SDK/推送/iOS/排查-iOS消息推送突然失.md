---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 推送
platform: iOS
title: iOS消息推送突然失效
root_cause: APNs证书问题导致DeviceToken无效
solution: 检查APNs证书配置，确保证书与打包环境匹配（开发/生产），参考文档排查BadDeviceToken问题
customers: ["南昌市闲得无聊文化有限公司"]
source: chat_history
tags: ["iOS推送", "BadDeviceToken", "证书", "推送失效"]
created: 2025-02-20
updated: 2026-03-20
---

## 问题：iOS iOS消息推送突然失效

## 问题详情

**现象**：
iOS的云信消息推送突然没有了，证书看起来正常，之前能收到，前天突然收不到。

## 排查过程

1. 检查证书配置 → 看起来正常
2. 对比测试 → 真机运行能收到，线上收不到
3. 拉取日志分析 → 发现BadDeviceToken错误

## 问题原因

APNs证书问题导致DeviceToken无效

## 解决方案

检查APNs证书配置，确保证书与打包环境匹配（开发/生产），参考文档排查BadDeviceToken问题

## 其他触发场景
- [iOS] iOS消息推送突然失效，来源：['南昌市闲得无聊文化有限公司']，2026-03-20
- [iOS] iOS消息推送突然失效，来源：['南昌市闲得无聊文化有限公司']，2026-03-20

