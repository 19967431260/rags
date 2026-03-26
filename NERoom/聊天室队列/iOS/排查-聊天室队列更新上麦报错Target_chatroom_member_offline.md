---
track_type: 排查类
sub_type: 集成类
product: NERoom
feature: 聊天室队列
platform: iOS
title: 聊天室队列更新上麦报错Target chatroom member offline
root_cause: 调用聊天室队列上麦接口前，操作者必须已在聊天室中；当前客户端未集成，无法加入聊天室
solution: 先用聊天室创建者accid统一操作队列完成调试；正常业务流程中用户上麦前需先加入聊天室。
customers: ["南京鹏珂互娱信息科技有限公司"]
source: chat_history
tags: ["聊天室队列", "上麦", "Target chatroom member offline"]
created: 2025-08-14
updated: 2026-03-26
---

## 问题：iOS 聊天室队列更新上麦报错Target chatroom member offline

## 问题详情

**现象**：
客户通过服务端调用聊天室队列上麦接口，B用户报错Target chatroom member offline，而A用户创建直播间后上麦正常。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
Target chatroom member offline

## 排查过程

1. 确认：报错是因为B用户不在聊天室里 → 定位成员状态问题
2. 确认：B用户还没接入客户端，还没加入聊天室 → 确认业务流程问题
3. 解决方案：先用聊天室创建者accid统一操作队列 → 临时解决方案

**关键发现**：调用聊天室队列上麦接口前，操作者必须已在聊天室中

## 问题原因

调用聊天室队列上麦接口前，操作者必须已在聊天室中；当前客户端未集成，无法加入聊天室

## 解决方案

先用聊天室创建者accid统一操作队列完成调试；正常业务流程中用户上麦前需先加入聊天室。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
