---
track_type: 排查类
sub_type: 功能实现咨询
product: IM-SDK
feature: 消息查询
platform: Uniapp
title: getThreadMessageList获取不到消息
root_cause: 混淆了thread消息和普通历史消息接口
solution: getThreadMessageList是获取回复的根消息（thread消息），普通历史消息应该使用getMessageList接口
customers: ["长沙兴超教育咨询有限公司"]
source: chat_history
tags: ["IM V10","Uniapp","历史消息","thread消息"]
created: 2025-05-05
updated: 2025-03-23
---

## 问题：Uniapp getThreadMessageList获取不到消息

## 问题详情

**现象**：
客户发送消息成功后，使用getThreadMessageList获取不到刚才发的消息。

**环境信息**：
- 平台：Uniapp
- 功能：消息查询

## 排查过程

1. 确认问题现象 → getThreadMessageList获取不到消息
2. 分析接口用途 → getThreadMessageList是获取回复的根消息
3. 提供正确接口 → 普通历史消息使用getMessageList

**关键发现**：混淆了thread消息和普通历史消息接口

## 问题原因

getThreadMessageList是获取回复的根消息（thread消息），不是用来获取普通历史消息的。

## 解决方案

getThreadMessageList是获取回复的根消息（thread消息），普通历史消息应该使用getMessageList接口。

## 其他触发场景

