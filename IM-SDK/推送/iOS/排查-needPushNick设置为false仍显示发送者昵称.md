---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: iOS
title: needPushNick设置为false仍显示发送者昵称
root_cause: forcepush字段配置会覆盖needPushNick设置，导致昵称仍然显示
solution: 除了needPushNick设置为false外，forcepush字段不要配置为true，否则forcepush会覆盖昵称隐藏设置
customers: ["VIP云信-上海导毕教育科技有限公司长沙分公司"]
source: chat_history
tags: ["iOS", "推送", "needPushNick", "forcepush", "昵称", "群聊"]
created: 2025-11-19
updated: 2026-03-20
---

## 问题：iOS needPushNick设置为false仍显示发送者昵称

## 问题详情

**现象**：
iOS设置needPushNick为false，对方手机收到的推送还是显示名字；群聊消息退后台和杀进程都显示昵称

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供消息ID查询 → 发现消息配置的是true
2. 建议new一个新的pushConfig对象赋值
3. 检查forcepushlist字段配置 → 发现配置了forcePush
4. 建议不配置forcepush字段

**关键发现**：

## 问题原因

forcepush字段配置会覆盖needPushNick设置，导致昵称仍然显示

## 解决方案

除了needPushNick设置为false外，forcepush字段不要配置为true，否则forcepush会覆盖昵称隐藏设置

## 其他触发场景

