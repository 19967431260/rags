---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 集成配置
platform: Android
title: Android Manifest自启动权限配置问题
root_cause: ""
solution: 在AndroidManifest.xml中对相关权限和组件添加tools:node="remove"去除，避免自启动。参考文档：https://doc.yunxin.163.com/messaging/guide/Tg3NDExMDA?platform=android
customers: ["北京耘想科技"]
source: chat_history
tags: ["Android", "Manifest", "自启动", "权限配置", "tools:node"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：Android Manifest自启动权限配置问题

## 问题详情

**现象**：
Android集成IM SDK后，Manifest中存在自启动相关配置导致问题

## 解决方案

在AndroidManifest.xml中对相关权限和组件添加tools:node="remove"去除，避免自启动。

参考文档：https://doc.yunxin.163.com/messaging/guide/Tg3NDExMDA?platform=android

## 其他触发场景

