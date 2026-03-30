---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 离线推送
platform: Android
title: 厂商推送SDK未注册成功导致收不到推送
root_cause: 客户端未成功注册厂商推送SDK，可能是集成问题或配置参数错误（如vivo的api_key和app_id）。
solution: 1. 检查厂商推送SDK集成是否正确；2. 核对AndroidManifest.xml中的厂商参数（api_key、app_id等）是否与厂商后台一致；3.
  查看SDK日志确认注册失败原因；4. vivo推送state=10004表示注册失败，需要检查配置。
customers:
- fusu
source: chat_history
tags:
- 厂商推送
- SDK注册
- vivo
- OPPO
- 华为
created: '2026-01-04'
updated: '2026-03-15'
---

## 问题：Android 厂商推送SDK未注册成功导致收不到推送

## 问题详情

**现象**：
vivo、OPPO、华为手机收不到离线推送。查询推送记录发现用户未注册对应厂商推送SDK。

## 排查过程

1. 查询推送记录 → 发现用户未注册厂商推送SDK
2. 检查客户端集成 → 需要确认厂商推送SDK集成和参数配置
**关键发现**：客户端未成功注册厂商推送SDK，导致无法获取token。

## 问题原因

客户端未成功注册厂商推送SDK，可能是集成问题或配置参数错误（如vivo的api_key和app_id）。

## 解决方案

1. 检查厂商推送SDK集成是否正确；2. 核对AndroidManifest.xml中的厂商参数（api_key、app_id等）是否与厂商后台一致；3. 查看SDK日志确认注册失败原因；4. vivo推送state=10004表示注册失败，需要检查配置。
