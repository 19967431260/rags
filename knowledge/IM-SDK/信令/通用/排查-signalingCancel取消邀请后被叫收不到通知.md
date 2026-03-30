---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "信令"
platform: "通用"
title: "signalingCancel取消邀请后被叫收不到通知"
root_cause: "待排查"
solution: "需要获取邀请方和被邀请方的完整console日志进行排查，日志获取方法参考：https://faq.yunxin.163.com/#KB0179"
customers: ["政采云"]
source: "chat_history"
tags: ["signalingCancel", "信令", "取消邀请", "通知"]
created: "2025-09-01"
updated: "2026-03-20"
---

## 问题：通用 signalingCancel取消邀请后被叫收不到通知

## 问题详情

**现象**：
使用signalingCall创建频道并邀请加入后，主叫用signalingCancel取消邀请，被叫收不到取消邀请的事件通知

## 排查过程

1. 确认问题现象 → 被叫收不到取消邀请通知
2. 检查是否超时 → 确认未超过120秒
3. 获取日志 → 需要双方完整console日志排查
**关键发现**：问题待进一步排查，需要日志确认

## 问题原因

待排查

## 解决方案

需要获取邀请方和被邀请方的完整console日志进行排查，日志获取方法参考：https://faq.yunxin.163.com/#KB0179

## 其他触发场景
