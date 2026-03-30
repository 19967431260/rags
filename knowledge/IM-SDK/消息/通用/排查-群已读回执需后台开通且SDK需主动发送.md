---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息
platform: 通用
title: 群已读回执需后台开通且SDK需主动发送
root_cause: 群已读回执功能未在管理后台开通，导致SDK调用时返回forbidden错误。
solution: 1. 在云信管理后台开通群已读回执功能（应用管理->应用配置->消息抄送->抄送类型->群消息已读回执）\n2. 已读回执需客户端主动调用SDK接口发送，SDK不会自动触发。B向A发送已读回执后，A会收到通知，表示该消息之前的消息均已被阅读。参考文档：https://doc.yunxin.163.com/messaging2/guide/TA5NjI1MzU?platform=client
customers: ["山东数拍","武汉毅麦信息科技有限公司"]
source: chat_history
tags: ["已读回执","v2GetTeamMessageReceipts","403","群已读回执","SDK主动发送"]
created: 2025-08-08
updated: 2026-03-26
---

## 问题：通用 群已读回执需后台开通且SDK需主动发送

## 问题详情

**现象**：
客户调用群消息回执接口时报403 forbidden错误（PIN function disabled / v2GetTeamMessageReceipts）。客户还询问已读回执SDK是否自动触发。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认接口报错信息 → 403 forbidden
2. 确认后台未开通群已读回执功能 → 根因

**关键发现**：群已读回执功能未在管理后台开通，导致SDK调用时返回forbidden错误。

## 问题原因

群已读回执功能未在管理后台开通，导致SDK调用时返回forbidden错误。

## 解决方案

1. 在云信管理后台开通群已读回执功能（应用管理->应用配置->消息抄送->抄送类型->群消息已读回执）
2. 已读回执需客户端主动调用SDK接口发送，SDK不会自动触发。B向A发送已读回执后，A会收到通知，表示该消息之前的消息均已被阅读。参考文档：https://doc.yunxin.163.com/messaging2/guide/TA5NjI1MzU?platform=client

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
