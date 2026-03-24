---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: 服务端
title: 华为推送title显示乱码问题
root_cause: 未配置pushTitle字段，默认使用群名称作为推送标题导致
solution: 发送消息时在payload中配置pushTitle字段指定推送标题，优先级最高
customers: ['成方金融科技有限公司']
source: chat_history
tags: ['华为推送', 'title乱码', 'pushTitle', '推送配置']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：华为推送title显示乱码问题

## 问题详情

**现象**：
华为推送收到的消息title显示乱码，客户怀疑是云信推送时编码问题导致。经排查发现是群名称作为默认推送标题时显示异常。

## 排查过程

1. 客户反馈华为推送收到乱码title
2. 技术支持确认推送title的取值逻辑
3. 发现群名称作为默认推送标题存在问题
4. 建议客户在发送消息时通过payload配置pushTitle字段

## 问题原因

未配置pushTitle字段，默认使用群名称作为推送标题导致

## 解决方案

发送消息时在payload中配置pushTitle字段指定推送标题，优先级最高

## 其他触发场景

（合并时在此处追加）
