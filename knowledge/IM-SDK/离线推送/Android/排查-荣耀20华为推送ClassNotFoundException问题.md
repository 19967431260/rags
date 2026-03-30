---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 离线推送
platform: Android
title: 荣耀20华为推送ClassNotFoundException问题
root_cause: 客户集成华为推送时使用了错误的依赖包（hwid），应该使用push包。老荣耀设备不支持荣耀推送，只支持华为推送。
solution: 集成华为推送应该使用com.huawei.hms:push:6.12.0.300，而不是hwid。同时需要在混淆配置中添加华为推送的keep规则。
customers: ["杭州知聊"]
source: chat_history
tags: ["华为推送", "荣耀", "ClassNotFoundException", "HmsInstanceId", "hwid", "push"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：荣耀20华为推送ClassNotFoundException问题

## 问题详情

**现象**：
荣耀20测试机器上出现崩溃：java.lang.NoClassDefFoundError: Failed resolution of: Lcom/huawei/hms/aaid/HmsInstanceId。云信版本9.19.4，华为hwid版本6.12.0.300。

**环境信息**：
- 平台：Android

## 排查过程

1. 确认客户同时接入了华为和荣耀推送SDK
2. 该荣耀20设备不支持荣耀推送（老设备）
3. 检查华为推送依赖，发现客户使用的是hwid而不是push包
4. 确认HmsInstanceId类在com.huawei.hms:opendevice包下，6.12.0.300版本没有opendevice包

## 根因分析

客户集成华为推送时使用了错误的依赖包（hwid），应该使用push包。老荣耀设备不支持荣耀推送，只支持华为推送。

## 解决方案

集成华为推送应该使用com.huawei.hms:push:6.12.0.300，而不是hwid。同时需要在混淆配置中添加华为推送的keep规则。

## 其他触发场景

（无）
