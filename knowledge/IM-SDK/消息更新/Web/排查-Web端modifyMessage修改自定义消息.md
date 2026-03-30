---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息更新
platform: Web
title: Web端modifyMessage修改自定义消息
root_cause: attachment字段传参格式错误，不能直接转为字符串
solution: attachment字段需要保持对象格式传入，不能转为字符串
customers: ['VIP云信-浙江恒信郃讯科技有限公司']
source: chat_history
tags: ['modifyMessage', '自定义消息', 'attachment', 'Web']
created: 2025-01-19
updated: 2026-03-23
---

## 问题：Web Web端modifyMessage修改自定义消息

## 问题详情

**现象**：
客户使用Web端modifyMessage接口修改已发送的自定义消息，修改text成功但修改attachment报错。

## 排查过程

1. 客户尝试修改自定义消息的attachment字段
2. 接口调用报错
**关键发现**：attachment字段不能直接转字符串传入

## 问题原因

attachment字段传参格式错误，不能直接转为字符串

## 解决方案

attachment字段需要保持对象格式传入，不能转为字符串

## 其他触发场景

（合并时在此处追加）
