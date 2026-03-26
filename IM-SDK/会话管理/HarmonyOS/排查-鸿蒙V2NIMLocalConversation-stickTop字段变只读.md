---
track_type: 排查类
sub_type: 测试问题
product: IM-SDK
feature: 会话管理
platform: HarmonyOS
title: 鸿蒙V2NIMLocalConversation的stickTop字段变只读
root_cause: SDK 10.9.30开始V2NIMLocalConversation的stickTop改为只读，不再支持直接修改
solution: 使用stickTopConversation方法设置置顶（传入conversationId和stickTop=true），不要直接修改V2NIMLocalConversation对象的stickTop字段；回调成功则置顶生效
customers: ["上海抱朴"]
source: chat_history
tags: ["HarmonyOS", "stickTop", "stickTopConversation", "SDK升级", "V2NIMLocalConversation"]
created: 2025-07-25
updated: 2025-07-25
---

## 问题：HarmonyOS V2NIMLocalConversation的stickTop字段变只读

## 问题详情

**现象**：
客户升级到SDK 10.9.30版本后，发现V2NIMLocalConversation中的stickTop变成readonly，无法直接修改；调用stickTopConversation方法置顶后，debug发现conversation中stickTop仍为false。

**复现步骤**：
1. 升级SDK到10.9.30版本
2. 尝试直接修改V2NIMLocalConversation对象的stickTop字段值
3. 发现字段为readonly，无法赋值

## 排查过程

1. 客户提供debug截图，确认V2NIMLocalConversation的stickTop为readonly
2. 确认为SDK升级后行为变化
3. 确认为本地缓存的conversation对象未被刷新
4. 建议检查stickTopConversation的回调结果

**关键发现**：SDK 10.9.30版本开始，V2NIMLocalConversation的stickTop字段改为只读属性，必须通过API方法修改。

## 问题原因

SDK 10.9.30版本对stickTop字段调整为只读，不再支持直接对象赋值修改。

## 解决方案

1. 使用stickTopConversation方法设置置顶：传入conversationId和stickTop=true
2. 不要直接修改V2NIMLocalConversation对象的stickTop字段
3. 确认回调结果为成功状态（回调中返回结果需检查success状态）
4. 置顶成功后，通过刷新会话列表获取最新的conversation对象
