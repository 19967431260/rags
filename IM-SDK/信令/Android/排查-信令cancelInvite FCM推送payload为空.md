---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 信令
platform: Android
title: 信令cancelInvite FCM推送payload为空
root_cause: cancelInvite接口目前不会透传配置的payload字段，推送使用默认文案。
solution: cancelInvite目前无法配置pushcontent和payload，默认推送文案无法修改或关闭。建议通过自定义推送文案处理，或等待产品需求评估。
customers: ['凯旋出海']
source: chat_history
tags: ['信令', 'cancelInvite', 'FCM', 'payload', '推送']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：Android 信令cancelInvite FCM推送payload为空

## 问题详情

**现象**：
客户使用信令实现音视频通话，invite时FCM推送正常，cancelInvite时FCM推送payload为空，导致显示默认中文文案。

## 排查过程

1. 客户反馈cancelInvite后收到FCM消息但payload为空 → 技术支持检查invite和cancelInvite配置
2. 客户确认cancelInvite加了payload → 技术支持查询确认触发两条推送
3. 技术支持发现cancelInvite实际未传递payload参数
4. 与研发确认cancelInvite不会透传payload字段

## 问题原因

cancelInvite接口目前不会透传配置的payload字段，推送使用默认文案。

## 解决方案

cancelInvite目前无法配置pushcontent和payload，默认推送文案无法修改或关闭。建议通过自定义推送文案处理，或等待产品需求评估。

## 其他触发场景

（合并时在此处追加）
