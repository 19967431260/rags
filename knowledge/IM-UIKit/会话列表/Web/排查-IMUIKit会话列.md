---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 会话列表
platform: Web
title: IM UIKit会话列表多次渲染导致页面卡顿
root_cause: 使用了多个ConversationContainer组件导致重复渲染
solution: 1. 不使用UIKit列表模块，直接调用数据层接口自行渲染
2. 或源码集成im-kit-ui，修改teamConversations/p2pConversations等关键词实现分栏
3. 用yarn build打包，产物复制到vue工程使用
customers: ["青岛和顺百鸿"]
source: chat_history
tags: ["IM-UIKit", "Web", "会话列表", "渲染性能", "卡顿"]
created: 2025-02-14
updated: 2026-03-20
---

## 问题：Web IM UIKit会话列表多次渲染导致页面卡顿

## 问题详情

**现象**：
自定义会话列表时，发送消息等操作会引起会话列表多次渲染，导致页面卡顿，业务无法忍受。

## 排查过程

1. 客户反馈自定义会话列表时发送消息等操作导致多次渲染
2. 建议客户不使用UIKit的列表模块，直接拿底层数据自行渲染
3. 研发分析发现使用了多个ConversationContainer导致
4. 提供源码修改方案，改成两个分栏样式

## 问题原因

使用了多个ConversationContainer组件导致重复渲染

## 解决方案

1. 不使用UIKit列表模块，直接调用数据层接口自行渲染
2. 或源码集成im-kit-ui，修改teamConversations/p2pConversations等关键词实现分栏
3. 用yarn build打包，产物复制到vue工程使用

## 其他触发场景

