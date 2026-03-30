---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 消息发送
platform: Android
title: V10 UIKit发送消息报错191004 invalid param
root_cause: 使用v10 UIKit但会话列表使用v9的本地会话接口，v10使用云端会话逻辑，混用导致参数错误。
solution: v10 UIKit所有逻辑必须走v10，包括会话列表获取。v9和v10能互通但不建议混用，建议统一升级到v10。
customers: ['武汉友趣网络科技']
source: chat_history
tags: ['V10', 'UIKit', '191004', 'invalid param', '会话', 'Android']
created: 2025-02-10
updated: 2026-03-23
---

## 问题：Android V10 UIKit发送消息报错191004 invalid param

## 问题详情

**现象**：
使用V10 UIKit跳转到消息页面后发送消息报错：Code=191004 invalid param。

**环境信息**：
- 平台：Android
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认发送方式 → 手动输入文本发送
2. 检查初始化配置 → 发现使用v2设置yes
3. 检查会话列表获取方式 → 发现使用v9的本地会话接口
4. 确认问题 → v10使用云端会话，客户混用v9本地会话接口导致
**关键发现**：v10 UIKit与v9会话接口混用导致参数错误

## 问题原因

使用v10 UIKit但会话列表使用v9的本地会话接口，v10使用云端会话逻辑，混用导致参数错误。

## 解决方案

v10 UIKit所有逻辑必须走v10，包括会话列表获取。v9和v10能互通但不建议混用，建议统一升级到v10。

## 其他触发场景

（合并时在此处追加：`- [Android] V10 UIKit发送消息报错191004 invalid param，来源：['武汉友趣网络科技']，2026-03-23`）
