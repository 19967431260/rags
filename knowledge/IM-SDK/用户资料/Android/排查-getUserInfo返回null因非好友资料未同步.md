---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 用户资料
platform: Android
title: getUserInfo返回null因非好友资料未同步
root_cause: 账号5381与查询方5377不是SDK好友关系，非好友时用户资料未同步，因此getUserInfo返回null
solution: 使用fetchUserInfo接口从云端拉取用户资料，可解决非好友关系下资料查询不到的问题
customers: ["必腾移动"]
source: chat_history
tags: ["getUserInfo","fetchUserInfo","用户资料","非好友","null"]
created: 2025-08-26
updated: 2025-08-26
---

## 问题：Android getUserInfo返回null因非好友资料未同步

## 问题详情

**现象**：
Android端通过NIMClient.getService(UserService.class).getUserInfo(contactId)获取用户信息，部分账号返回null（contactId: 5381，其他用户可正常查到）。SDK日志显示19点后无getUserInfo调用记录，需提供正确日志排查。

**复现步骤**：
（无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：contactId: 5381，与查询方5377

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服要求提供正确设备SDK日志
2. 客户提供复现日志后确认：5381和5377不是好友关系
3. 非SDK好友关系时，用户资料同步时机未到，导致查不到

**关键发现**：账号5381与查询方5377不是SDK好友关系，非好友时用户资料未同步，因此getUserInfo返回null。

## 问题原因

账号5381与查询方5377不是SDK好友关系，非好友时用户资料未同步，因此getUserInfo返回null。

## 解决方案

使用fetchUserInfo接口从云端拉取用户资料，可解决非好友关系下资料查询不到的问题。

## 其他触发场景

（合并时在此处追加）
