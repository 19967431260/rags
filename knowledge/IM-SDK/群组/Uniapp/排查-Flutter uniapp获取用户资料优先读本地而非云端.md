---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组
platform: Uniapp
title: Flutter uniapp获取用户资料优先读本地而非云端
root_cause: getUserList接口优先从客户端本地获取数据，不会自动拉取云端最新资料。
solution: 需要从云端获取最新用户资料时，应调用getUserListFromCloud接口，而非getUserList。
customers: ["山东数拍"]
source: chat_history
tags: ["getUserList","getUserListFromCloud","Flutter","用户资料","云端"]
created: 2025-08-09
updated: 2026-03-26
---

## 问题：Uniapp Flutter uniapp获取用户资料优先读本地而非云端

## 问题详情

**现象**：
客户Flutter端调用NimCore.instance.userService.getUserList([accountId])返回的用户资料不全，询问是否能从云端获取最新用户数据。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认接口行为 → getUserList 优先本地

**关键发现**：getUserList接口优先从客户端本地获取数据，不会自动拉取云端最新资料。

## 问题原因

getUserList接口优先从客户端本地获取数据，不会自动拉取云端最新资料。

## 解决方案

需要从云端获取最新用户资料时，应调用getUserListFromCloud接口，而非getUserList。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
