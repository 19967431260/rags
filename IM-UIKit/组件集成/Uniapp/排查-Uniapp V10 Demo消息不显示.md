---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 组件集成
platform: Uniapp
title: Uniapp V10 Demo消息不显示
root_cause: V10版本需要开启云端会话功能，且Uniapp应使用V9版本的UIKit
solution: Uniapp项目使用V9版本UIKit，参考: https://github.com/netease-kit/nim-uikit-uniapp/tree/release/1.5.0；如需使用V10需要开启云端会话
customers: ['VIP云信-云南国云药材国际交易有限公司']
source: chat_history
tags: ['UIKit', 'Uniapp', 'V10', 'V9', '云端会话']
created: 2025-02-20
updated: 2026-03-23
---

## 问题：Uniapp Uniapp V10 Demo消息不显示

## 问题详情

**现象**：
运行官方V10 Uniapp Demo时，消息列表显示不出来，但实际有消息

**环境信息**：
- 平台：Uniapp
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户使用Web端已有账号测试
2. 检查发现客户跑的是V10 Demo但账号是V9版本
**关键发现**：V10版本需要开启云端会话，且Uniapp应使用V9版本

## 问题原因

V10版本需要开启云端会话功能，且Uniapp应使用V9版本的UIKit

## 解决方案

Uniapp项目使用V9版本UIKit，参考: https://github.com/netease-kit/nim-uikit-uniapp/tree/release/1.5.0；如需使用V10需要开启云端会话

## 其他触发场景

（合并时在此处追加：`- [Uniapp] Uniapp V10 Demo消息不显示，来源：['VIP云信-云南国云药材国际交易有限公司']，2026-03-23`）
