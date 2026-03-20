---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Android
title: vivo推送隐私声明配置导致无法获取token
root_cause: 未获得用户隐私许可（agreePrivacyStatement）
solution: 将vivo推送配置中的agreePrivacyStatement设置为true
customers: ["上海掌鑫聚芯信息科技有限公司"]
source: chat_history
tags: ["vivo推送", "隐私声明", "agreePrivacyStatement", "token"]
created: 2025-11-14
updated: 2026-03-20
---

## 问题：Android vivo推送隐私声明配置导致无法获取token

## 问题详情

**现象**：
vivo推送配置后无法获取token，日志显示agreePrivacyStatement=false。

**排查过程**：
1. 检查日志发现agreePrivacyStatement=false
2. 确认需要用户隐私许可后才能开启推送

## 问题原因

未获得用户隐私许可（agreePrivacyStatement）

## 解决方案

将vivo推送配置中的agreePrivacyStatement设置为true
