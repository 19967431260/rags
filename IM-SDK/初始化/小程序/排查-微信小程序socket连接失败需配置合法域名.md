---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: 小程序
title: 微信小程序socket连接失败需配置合法域名
root_cause: 小程序初始化代码未加上默认的lbs和link配置
solution: 小程序需要在初始化代码中加上默认的lbs和link配置，参考文档：https://doc.yunxin.163.com/messaging/guide/zIyNzIwOTc?platform=miniProgram
customers: ["VIP-云信-深圳蜜蜂互联"]
source: chat_history
tags: ["微信小程序", "socket", "合法域名", "lbs", "link", "初始化配置"]
created: 2025-11-20
updated: 2026-03-20
---

## 问题：小程序 微信小程序socket连接失败需配置合法域名

## 问题详情

**现象**：
微信小程序socket突然连不上，需要配置合法域名；已参考文档配置但报错

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供报错截图 → 发现域名配置不完整
2. 检查初始化代码 → 发现缺少lbs和link配置

**关键发现**：

## 问题原因

小程序初始化代码未加上默认的lbs和link配置

## 解决方案

小程序需要在初始化代码中加上默认的lbs和link配置，参考文档：https://doc.yunxin.163.com/messaging/guide/zIyNzIwOTc?platform=miniProgram

## 其他触发场景

