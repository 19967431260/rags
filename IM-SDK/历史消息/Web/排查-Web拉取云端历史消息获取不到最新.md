---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 历史消息
platform: Web
title: Web拉取云端历史消息获取不到最新
root_cause: reverse参数设置不正确，默认false表示从endTime往前查找，true表示从beginTime往后查找
solution: 将reverse改为false，从endTime开始往前查找历史消息
customers: ["VIP云信-武汉量子千寻科技有限公司"]
source: chat_history
tags: ["Web", "历史消息", "云端", "reverse", "getHistoryMsgs"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：Web拉取云端历史消息获取不到最新

## 问题详情

**现象**：
Web端从云端拉取历史消息时，获取不到最新的消息记录

**环境信息**：
- 平台：Web

## 排查过程

1. 客户反馈拉取不到最新消息
2. 检查参数发现reverse设置问题
3. 建议将reverse改为false
4. 测试验证成功

## 根因分析

reverse参数设置不正确，默认false表示从endTime往前查找，true表示从beginTime往后查找

## 解决方案

将reverse改为false，从endTime开始往前查找历史消息

## 其他触发场景

（无）
