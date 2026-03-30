---
track_type: 排查类
sub_type: BUG问题
product: IM-SDK
feature: 消息过滤
platform: HarmonyOS
title: 鸿蒙SDK拉取线上消息过滤器中attachment为null问题
root_cause: 鸿蒙SDK拉取云端消息时，过滤器中attachment字段未正确赋值
solution: 问题已确认，研发定位中，后续版本修复
customers: ['ISV云信私有化-顺丰科技-多项目']
source: chat_history
tags: ['鸿蒙', '消息过滤', 'attachment', '拉取云端消息']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：HarmonyOS 鸿蒙SDK拉取线上消息过滤器中attachment为null问题

## 问题详情

**现象**：
客户反馈鸿蒙SDK拉取线上消息时走消息过滤逻辑，但过滤器中message的attachment没有值，导致过滤失败。

## 排查过程

1. 客户确认拉线上消息会走消息过滤
2. 发现过滤器中message.attachment为null
3. 但message._attachment是有值的
4. 技术支持确认问题，研发定位中

## 问题原因

鸿蒙SDK拉取云端消息时，过滤器中attachment字段未正确赋值

## 解决方案

问题已确认，研发定位中，后续版本修复

## 其他触发场景

（合并时在此处追加）
