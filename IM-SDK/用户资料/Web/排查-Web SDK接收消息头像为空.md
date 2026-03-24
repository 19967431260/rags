---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 用户资料
platform: Web
title: Web SDK接收消息头像为空
root_cause: SDK采用按需拉取策略，不会自动同步所有用户资料，需要主动调用接口获取。
solution: 需要根据会话id主动调用接口获取用户资料，或手动触发用户资料更新。参考文档：https://faq.yunxin.163.com/#KB0039
customers: ['VIP云信-武汉自由无限科技有限公司']
source: chat_history
tags: ['头像', '用户资料', 'Web SDK', 'getConversationList', '按需拉取']
created: 2025-02-08
updated: 2026-03-23
---

## 问题：Web Web SDK接收消息头像为空

## 问题详情

**现象**：
使用Web SDK(nim-web-sdk-ng 10.7.1)接收消息时，发送方有头像但接收到的avatar字段为空，会话列表也缺少头像信息。

**环境信息**：
- 平台：Web
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认用户资料更新时机 → SDK按需拉取用户资料
2. 手动调用获取用户资料接口后头像正常显示

## 问题原因

SDK采用按需拉取策略，不会自动同步所有用户资料，需要主动调用接口获取。

## 解决方案

需要根据会话id主动调用接口获取用户资料，或手动触发用户资料更新。参考文档：https://faq.yunxin.163.com/#KB0039

## 其他触发场景

（合并时在此处追加：`- [Web] Web SDK接收消息头像为空，来源：['VIP云信-武汉自由无限科技有限公司']，2026-03-23`）
