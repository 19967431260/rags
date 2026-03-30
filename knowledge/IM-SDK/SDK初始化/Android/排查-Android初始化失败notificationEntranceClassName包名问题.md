---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: SDK初始化
platform: Android
title: Android新包初始化失败：notificationEntranceClassName包名未改
root_cause: 新打包时notificationEntranceClassName配置的包名未更新为新包的包名，导致初始化失败
solution: 修改notificationEntranceClassName中配置的包名为新包的实际包名，重新打包即可。
customers: ["Melvo-云信-项目对接群"]
source: chat_history
tags: ["Android", "初始化失败", "notificationEntranceClassName", "包名"]
created: 2025-07-11
updated: 2025-07-25
---

## 问题：Android新包初始化失败：notificationEntranceClassName包名未改

## 问题详情

**现象**：

## 问题原因

新打包时notificationEntranceClassName配置的包名未更新为新包的包名，导致初始化失败

## 解决方案

修改notificationEntranceClassName中配置的包名为新包的实际包名，重新打包即可。
