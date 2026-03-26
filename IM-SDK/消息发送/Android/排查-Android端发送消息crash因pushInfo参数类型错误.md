---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 消息发送
platform: Android
title: Android端发送消息crash因pushInfo参数类型错误
root_cause: 发送消息时pushInfo字段传了字符串"null"而非整数或省略，JSON解析时类型不匹配导致崩溃
solution: 发送消息接口中pushInfo字段应传整型（或不传，后端会自动补充），不能传字符串"null"。修改方法：去掉该字段，或传入正确的整数值。
customers: ["郑州晨宙信息科技有限公司"]
source: chat_history
tags: ["crash", "Android", "pushInfo", "JSON解析", "消息发送"]
created: 2025-08-11
updated: 2026-03-26
---

## 问题：Android Android端发送消息crash因pushInfo参数类型错误

## 问题详情

**现象**：
客户在Android端发送消息时发生崩溃（crash），截图显示崩溃发生在消息发送流程中。客户不知道具体哪个参数有问题。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服查看日志，判断是JSON解析传入参数时崩溃 → 初步判断JSON解析问题
2. 客服要求客户提供传入的完整消息JSON数据 → 获取完整数据
3. 客户提供后，客服发现pushInfo字段值为字符串"null"（而非不传或传整数） → 定位根因
4. 客服确认pushInfo应传整型，让客户去掉该字段测试 → 提供解决方案
5. 客户去掉后确认正常 → 问题解决

**关键发现**：pushInfo字段传了字符串"null"而非整数或省略，JSON解析时类型不匹配导致崩溃

## 问题原因

发送消息时pushInfo字段传了字符串"null"而非整数或省略，JSON解析时类型不匹配导致崩溃

## 解决方案

发送消息接口中pushInfo字段应传整型（或不传，后端会自动补充），不能传字符串"null"。修改方法：去掉该字段，或传入正确的整数值。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
