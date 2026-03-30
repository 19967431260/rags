---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: Flutter
title: Flutter自定义会话列表item左滑置顶删除无响应
root_cause: UIKit日志层不打印UI层记录，需要本地复现调试
solution: 将nim_chatkit_ui改为源码依赖，自行调试检查左滑菜单点击事件是否执行到相应代码逻辑
customers: ['中科智感（湛江）科技发展有限公司']
source: chat_history
tags: ['Flutter', 'UIKit', '会话列表', '左滑菜单', '置顶', '删除']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：Flutter Flutter自定义会话列表item左滑置顶删除无响应

## 问题详情

**现象**：
客户使用Flutter UIKit自定义会话列表，实现item左滑显示置顶和删除按钮，但点击后无响应。客户使用customItemBuilder自定义了会话列表项UI。

## 排查过程

1. 客户反馈Flutter自定义会话列表item左滑后，置顶和删除按钮点击无响应
2. 技术支持建议将UIKit改为本地源码依赖进行调试
3. 需要检查左滑菜单的点击事件是否正确绑定

## 问题原因

UIKit日志层不打印UI层记录，需要本地复现调试

## 解决方案

将nim_chatkit_ui改为源码依赖，自行调试检查左滑菜单点击事件是否执行到相应代码逻辑

## 其他触发场景

（合并时在此处追加）
