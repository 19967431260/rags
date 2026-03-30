---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 消息接收
platform: 小程序
title: 微信小程序图片消息不触发onMsg事件
root_cause: SDK里处理消息attach的函数在微信小程序环境使用了self，小程序环境下self为undefined导致消息处理失败
solution: 升级Web SDK到9.20.14版本即可修复该问题
customers: ["上海超旺信息科技有限公司"]
source: chat_history
tags: ["onMsg","图片消息","小程序","self","WebSocket","9.20.14"]
created: 2025-08-19
updated: 2026-03-26
---

## 问题：小程序 微信小程序图片消息不触发onMsg事件

## 问题详情

**现象**：
微信小程序使用Web SDK 9.20.12，图片消息不会触发onMsg事件，但与云信websocket连接正常收到消息。旧版本7.9.0正常。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：9.20.12（从会话提取）
- 系统版本 / 设备：微信小程序
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户反馈图片消息不触发onMsg但websocket收到 → 确认问题范围
2. 对比版本7.9.0正常，9.20.12异常 → 版本对比
3. 导出console日志分析，SDK内部processMsg报错excute failed → 定位报错位置
4. 进一步定位发现SDK处理消息attach的函数在微信小程序环境self为undefined → 根因定位
5. 研发确认问题并发布修复版本9.20.14 → 修复确认

**关键发现**：SDK里处理消息attach的函数在微信小程序环境使用了self，小程序环境下self为undefined导致消息处理失败

## 问题原因

SDK里处理消息attach的函数在微信小程序环境使用了self，小程序环境下self为undefined导致消息处理失败。

## 解决方案

升级Web SDK到9.20.14版本即可修复该问题。

## 其他触发场景

（合并时在此处追加）
