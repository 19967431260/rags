---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息管理
platform: Web
title: Web端聊天信息被安全通屏蔽：V10可用antispamConfig配置单条消息关闭
root_cause: 配置了安全通（im安全通），发送消息时被安全审核屏蔽
solution: Web端V10可通过V2NIMMessage的antispamConfig配置单条消息关闭安全通；如需整个应用都不想走反垃圾，需反馈给产研评估
customers: ["高途预见塔塔项目"]
source: chat_history
tags: ["Web端", "安全通", "antispamConfig", "V10", "单条消息", "屏蔽"]
created: 2025-06-30
updated: 2026-03-25
---

## 问题：Web端聊天信息被安全通屏蔽：V10可用antispamConfig配置单条消息关闭

## 问题原因

配置了安全通（im安全通），发送消息时被安全审核屏蔽

## 解决方案

Web端V10可通过V2NIMMessage的antispamConfig配置单条消息关闭安全通；如需整个应用都不想走反垃圾，需反馈给产研评估
