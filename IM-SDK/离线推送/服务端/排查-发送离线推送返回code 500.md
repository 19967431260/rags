---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "离线推送"
platform: "服务端"
title: "发送离线推送返回code 500"
root_cause: "payload中的notifyId字段需要是数字类型，但客户传的是字符串"
solution: "将notifyId改为数字类型"
customers: ["广州浪花"]
source: "chat_history"
tags: ["500", "离线推送", "notifyId", "payload"]
created: "2025-09-18"
updated: "2026-03-20"
---

## 问题：服务端 发送离线推送返回code 500

## 问题详情

**现象**：
发送离线推送消息时返回code 500，payload中包含pushTitle、notifyId、apsField、fcmFieldV1等字段。

## 排查过程

1. 客户提供发送时间、from accid、appkey
2. 技术人员核查发现payload中的notifyId格式错误

## 问题原因

payload中的notifyId字段需要是数字类型，但客户传的是字符串

## 解决方案

将notifyId改为数字类型

## 其他触发场景
