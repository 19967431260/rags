---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话回调
platform: HarmonyOS
title: 鸿蒙端删除本地会话后首次收消息未触发onConversationChanged
root_cause: 首次收到消息只触发onConversationCreated，不触发onConversationChanged
solution: 监听onDataSync数据同步完成后再一把更新会话列表UI，参考文档：https://doc.yunxin.163.com/messaging2/guide/Dk1MTY4MzA?platform=client#1-%E6%B3%A8%E5%86%8C%E7%99%BB%E5%BD%95%E7%8A%B6%E6%80%81%E7%9B%B8%E5%85%B3%E7%9B%91%E5%90%AC
customers: ["好未来-yach"]
source: chat_history
tags: ["onConversationChanged","onConversationCreated","onDataSync","鸿蒙"]
created: 2025-02-14
updated: 2025-03-20
---

## 问题：HarmonyOS 鸿蒙端删除本地会话后首次收消息未触发onConversationChanged

## 问题详情

**现象**：
删除一条本地会话后，别人发消息只触发了onConversationCreated和onReceiveMessages，没触发onConversationChanged，再发一条才触发。

## 排查过程

1. 分析首次收到消息触发onConversationCreated是否足够 → 评估影响
2. 建议增加监听onConversationCreated → 提供方案
3. 建议监听onDataSync数据同步完成后再更新会话列表UI → 最佳实践

**关键发现**：首次收到消息只触发onConversationCreated，不触发onConversationChanged

## 问题原因

首次收到消息只触发onConversationCreated，不触发onConversationChanged。

## 解决方案

监听onDataSync数据同步完成后再一把更新会话列表UI，参考文档：https://doc.yunxin.163.com/messaging2/guide/Dk1MTY4MzA?platform=client#1-%E6%B3%A8%E5%86%8C%E7%99%BB%E5%BD%95%E7%8A%B6%E6%80%81%E7%9B%B8%E5%85%B3%E7%9B%91%E5%90%AC

## 其他触发场景

