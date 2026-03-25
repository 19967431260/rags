---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息存储
platform: iOS
title: iOS端数据库损坏导致消息记录无法加载
root_cause: 本地数据库文件损坏，且备份数据库也损坏
solution: 卸载重装应用。建议开启sessionDatabaseBackupEnabled数据库备份功能，可在数据库损坏时恢复备份
customers: ["深圳市镜玩"]
source: chat_history
tags: ["IM-SDK", "数据库损坏", "消息记录", "iOS", "sessionDatabaseBackupEnabled"]
created: 2025-05-14
updated: 2025-03-20
---

## 问题：iOS iOS端数据库损坏导致消息记录无法加载

## 问题详情

**现象**：
iOS用户进入聊天界面后无法加载历史消息记录，刷新无效。

## 排查过程

**关键发现**：本地数据库文件损坏，且备份数据库也损坏

## 问题原因

本地数据库文件损坏，且备份数据库也损坏

## 解决方案

卸载重装应用。建议开启sessionDatabaseBackupEnabled数据库备份功能，可在数据库损坏时恢复备份
