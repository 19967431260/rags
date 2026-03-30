---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "会话置顶"
platform: "iOS"
title: "手动调用置顶API后会话未置顶"
root_cause: "手动置顶后需要确保onConversationChanged回调触发，才会刷新置顶列表UI"
solution: "检查addStickTop之后onConversationChanged会话变更是否触发，变更了就会走filterStickTopData更新置顶列表"
customers: ["北京兔玩在线"]
source: "chat_history"
tags: ["置顶", "addStickTop", "onConversationChanged", "iOS", "UIKit"]
created: "2025-09-23"
updated: "2026-03-20"
---

## 问题：iOS 手动调用置顶API后会话未置顶

## 问题详情

**现象**：
客户手动调用置顶API，但会话仍在原位置，只是背景色换成了置顶样式。

## 排查过程

1. 客户反馈手动调用置顶API后会话未置顶
2. 确认客户系统消息是单独加的，非UIKit本身会话
3. 建议检查addStickTop之后onConversationChanged会话变更是否触发
4. 变更后会走filterStickTopData刷新置顶数据

## 问题原因

手动置顶后需要确保onConversationChanged回调触发，才会刷新置顶列表UI

## 解决方案

检查addStickTop之后onConversationChanged会话变更是否触发，变更了就会走filterStickTopData更新置顶列表

## 其他触发场景
