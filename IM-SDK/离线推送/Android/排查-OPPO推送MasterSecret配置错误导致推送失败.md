---
track_type: 排查类
sub_type: 配置问题
product: IM-SDK
feature: 离线推送
platform: Android
title: OPPO推送MasterSecret配置错误导致推送失败
root_cause: 云信控制台配置的OPPO MasterSecret参数填写错误，该参数需要从OPPO推送控制台获取。
solution: 在OPPO推送控制台找到正确的MasterSecret，更新到云信控制台的厂商推送配置中。注意不要填错其他参数。
customers:
- fusu
source: chat_history
tags:
- OPPO推送
- MasterSecret
- 配置错误
created: '2026-01-04'
updated: '2026-03-15'
---

## 问题：Android OPPO推送MasterSecret配置错误导致推送失败

## 问题详情

**现象**：
OPPO手机收不到离线推送。检查推送记录发现推送失败。

## 排查过程

1. 查询推送记录 → 发现推送失败
2. 检查云信后台配置 → 发现MasterSecret填写错误
**关键发现**：云信后台配置的OPPO MasterSecret不正确。

## 问题原因

云信控制台配置的OPPO MasterSecret参数填写错误，该参数需要从OPPO推送控制台获取。

## 解决方案

在OPPO推送控制台找到正确的MasterSecret，更新到云信控制台的厂商推送配置中。注意不要填错其他参数。
