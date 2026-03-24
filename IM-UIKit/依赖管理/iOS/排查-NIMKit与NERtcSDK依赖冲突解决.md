---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 依赖管理
platform: iOS
title: NIMKit与NERtcSDK依赖冲突解决
root_cause: NIMKit/Full与NERtcSDK存在重复依赖
solution: 使用NIMKit/Lite替代NIMKit/Full，或源码依赖NIMKit后自行修改依赖
customers: ['重庆橙心物流网络']
source: chat_history
tags: ['iOS', 'NIMKit', 'NERtcSDK', '依赖冲突', 'pod', 'NIMKit/Lite']
created: 2025-02-12
updated: 2026-03-23
---

## 问题：iOS NIMKit与NERtcSDK依赖冲突解决

## 问题详情

**现象**：
NIMKit/Full与NERtcSDK同时集成时出现依赖冲突，客户之前通过先pod NIMKit/Full再删除重复依赖的方式解决，询问是否有更好的方法。

**环境信息**：
- 平台：iOS
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认问题：NIMKit/Full与NERtcSDK依赖冲突
2. 询问历史解决方案
3. 建议尝试NIMKit/Lite

## 问题原因

NIMKit/Full与NERtcSDK存在重复依赖

## 解决方案

使用NIMKit/Lite替代NIMKit/Full，或源码依赖NIMKit后自行修改依赖

## 其他触发场景

（合并时在此处追加：`- [iOS] NIMKit与NERtcSDK依赖冲突解决，来源：['重庆橙心物流网络']，2026-03-23`）
