---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Electron
title: Electron会话lastMessage与消息不一致问题
root_cause: Electron SDK在消息重复写入时会话lastMessage未正确更新
solution: 升级到10.6.0或之后版本修复该问题
customers: ['ISV云信私有化-顺丰科技-多项目']
source: chat_history
tags: ['Electron', 'lastMessage', '撤回消息', '会话']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Electron Electron会话lastMessage与消息不一致问题

## 问题详情

**现象**：
客户反馈Electron端撤回消息后，会话的lastMessage和实际消息内容对不上，msg_attach_显示错误。

## 排查过程

1. 客户反馈撤回消息后lastMessage未更新
2. 查看日志发现写入消息时提示duplicate msg_id
3. 技术支持确认是本地已有该消息，更新了状态
4. 但会话的lastMessage未同步更新
5. 确认是已知问题，建议升级到10.6.0之后版本

## 问题原因

Electron SDK在消息重复写入时会话lastMessage未正确更新

## 解决方案

升级到10.6.0或之后版本修复该问题

## 其他触发场景

（合并时在此处追加）
