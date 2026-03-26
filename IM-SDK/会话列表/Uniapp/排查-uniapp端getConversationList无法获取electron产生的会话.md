---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: Uniapp
title: uniapp端getConversationList无法获取electron产生的会话
root_cause: 本地会话未开启漫游消息同步开关，导致多端会话数据未同步到本地
solution: 到控制台开启「漫游消息」开关，开启后本地会话列表即可同步获取各端创建的会话
customers: ["上海文攸网络科技有限公司","芜湖市乖巧虎科技有限公司"]
source: chat_history
tags: ["getConversationList","Uniapp","会话列表","漫游消息"]
created: 2025-08-02
updated: 2026-03-26
---

## 问题：Uniapp uniapp端getConversationList无法获取electron产生的会话

## 问题详情

**现象**：
uniapp SDK调用getConversationList(本地会话)获取会话列表时：1）读不到electron客户端产生的会话，这些会话6小时内仍有聊天记录；2）新发消息后短期能读到，过一会就读不到了；3）uniapp自己创建的会话过半小时也读不到了。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：uniapp + electron 多端场景

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（无详细排查步骤，从会话提取）

**关键发现**：本地会话未开启漫游消息同步开关，导致多端会话数据未同步到本地

## 问题原因

本地会话未开启漫游消息同步开关，导致多端会话数据未同步到本地。

## 解决方案

到控制台开启「漫游消息」开关，开启后本地会话列表即可同步获取各端创建的会话。

## 其他触发场景

（合并时在此处追加）
