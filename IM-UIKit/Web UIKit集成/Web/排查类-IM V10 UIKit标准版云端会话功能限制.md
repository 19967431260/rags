---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: Web UIKit集成
platform: Web
title: IM V10 UIKit标准版云端会话功能限制
root_cause: V10 UIKit需要使用云端会话功能，但标准版应用无法开启云端会话功能。
solution: 标准版应用只能使用V9版本的UIKit（如9.8.0），或联系商务开通高级版应用以使用V10 UIKit。
customers: ['杭州泥鳅信息技术有限公司']
source: chat_history
tags: ['IM-UIKit', 'V10', '标准版', '云端会话', 'forbidden', 'Vue3']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：IM V10 UIKit标准版云端会话功能限制

## 问题详情

**现象**：
客户使用标准版应用集成V10 UIKit时，出现insertConversationActive failed: forbidden错误。

## 排查过程

1. 客户反馈登录后显示当前网络不可用
2. 检查发现使用的是V10 UIKit但云端会话功能未开启
3. 客户确认是IM2024标准版，无法开启云端会话
4. 建议切换到V9 SDK或联系商务开通高级版
5. 客户清理node_module后仍报错，发现还是用的V10版本
6. 最终建议降级到V9版本（9.8.0）

## 问题原因

V10 UIKit需要使用云端会话功能，但标准版应用无法开启云端会话功能。

## 解决方案

标准版应用只能使用V9版本的UIKit（如9.8.0），或联系商务开通高级版应用以使用V10 UIKit。

## 其他触发场景

（合并时在此处追加）
