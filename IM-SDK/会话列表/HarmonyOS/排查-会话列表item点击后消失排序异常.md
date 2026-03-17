---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: HarmonyOS
title: 会话列表item点击后消失排序异常
root_cause: 消息删除的多端通知导致会话创建时无lastMsg,后续获取到历史消息后会话时间戳更新为历史消息时间,排序逻辑将其排到底部
solution: 这是正常行为。会话排序逻辑:无lastMsg时使用conversation.updateTime,有lastMsg后使用lastMsg.createTime。建议优化排序策略或在UI层处理此场景。
customers: ["北京创新一号"]
source: chat_history
tags: ["会话列表", "排序异常", "lastMsg", "多端通知", "消息删除"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：HarmonyOS 会话列表item点击后消失排序异常

## 问题详情

**现象**：
鸿蒙端会话列表中,点击某个会话进入聊天界面后退出,该会话item从列表顶部消失。现象:用户10876408点击太行山用户(account:11212067)会话后退出,会话item不见了。

## 排查过程

1. 检查云端消息数据 → 云端有消息存在
2. 分析日志发现排查流程:
   - 登录成功后收到删除消息的多端通知,会话被创建但没有最后一条消息
   - 点进会话后获取云端消息,获取到7天前的消息并入库,触发会话变更
   - 退出后会话最后一条消息时间戳变为7天前,排序被排到列表最下方

**关键发现**:会话item未消失,而是因时间戳变化被排序到列表底部

## 问题原因

消息删除的多端通知导致会话创建时无lastMsg,后续获取到历史消息后会话时间戳更新为历史消息时间,排序逻辑将其排到底部

## 解决方案

这是正常行为。会话排序逻辑:无lastMsg时使用conversation.updateTime,有lastMsg后使用lastMsg.createTime。建议优化排序策略或在UI层处理此场景。

## 其他触发场景

（暂无）
