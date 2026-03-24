---
track_type: 排查类
sub_type: BUG问题
product: IM-SDK
feature: 群组管理
platform: HarmonyOS
title: 鸿蒙SDK转让群主后群信息获取异常问题
root_cause: 鸿蒙SDK在特定群操作场景下群信息同步异常
solution: 问题已确认，将在后续版本优化修复
customers: ['ISV云信私有化-顺丰科技-多项目']
source: chat_history
tags: ['鸿蒙', '转让群主', '群信息', '不在群内']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙SDK转让群主后群信息获取异常问题

## 问题详情

**现象**：
客户反馈鸿蒙SDK存在bug：A拉B创建群聊，A转让群主给B，A退出群聊后，B拉取的群信息显示自己不在群内。

## 排查过程

1. 客户提供必现操作路径
2. 复现步骤：A拉B创建群 -> A转让群主给B -> A退出群聊 -> B拉取群信息
3. B通过getMessageList接口拉取群信息
4. 技术支持确认问题，将在后续版本优化

## 问题原因

鸿蒙SDK在特定群操作场景下群信息同步异常

## 解决方案

问题已确认，将在后续版本优化修复

## 其他触发场景

（合并时在此处追加）
