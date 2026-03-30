---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 消息列表
platform: iOS
title: iOS语音或文字消息重复显示
root_cause: P2PChatViewController或其父类ChatViewController在返回上一页时未释放(deinit未执行)，导致消息回调被重复注册
solution: 在viewWillDisappear中执行clean操作，在viewWillAppear中添加监听，确保控制器释放时清理回调
customers: ['广州品爱科技']
source: chat_history
tags: ['消息重复', 'UIKit', 'iOS', '内存泄漏', 'ChatViewController', 'deinit']
created: 2025-01-18
updated: 2026-03-23
---

## 问题：iOS iOS语音或文字消息重复显示

## 问题详情

**现象**：
iOS端使用IM UIKit时，语音或文字信息出现重复显示的问题。

## 排查过程

1. 客户提供截图展示重复消息现象
2. 技术支持分析：ChatViewController返回上一页时没有释放，没有走deinit
3. 定位到发消息走了两次回调，导致发了两次消息
4. 建议修复方案

## 问题原因

P2PChatViewController或其父类ChatViewController在返回上一页时未释放(deinit未执行)，导致消息回调被重复注册

## 解决方案

在viewWillDisappear中执行clean操作，在viewWillAppear中添加监听，确保控制器释放时清理回调

## 其他触发场景

（合并时在此处追加）
