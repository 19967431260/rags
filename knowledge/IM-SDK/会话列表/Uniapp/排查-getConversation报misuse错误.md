---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: Uniapp
title: getConversation报misuse错误
root_cause: SDK 10.8.10开始默认使用本地会话，需要开启配置才能使用云端会话
solution: 初始化时添加enableV2CloudConversation配置开启云端会话。
customers: ["山西闪数科技有限公司"]
source: chat_history
tags: ["getConversation", "misuse", "本地会话", "云端会话", "enableV2CloudConversation"]
created: 2025-05-08
updated: 2025-03-20
---

## 问题：Uniapp getConversation报misuse错误

## 问题详情

**现象**：
登录状态正常，但getConversation/getConversationList获取会话报misuse错误。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Uniapp

## 排查过程

1. 确认SDK版本
2. 发现10.8.10开始默认使用本地会话
3. 需要开启配置才能使用云端会话

## 问题原因

SDK 10.8.10开始默认使用本地会话，需要开启配置才能使用云端会话

## 解决方案

初始化时添加enableV2CloudConversation配置开启云端会话。

## 其他触发场景

