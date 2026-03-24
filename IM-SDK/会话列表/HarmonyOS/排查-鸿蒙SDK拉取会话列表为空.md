---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: HarmonyOS
title: 鸿蒙SDK拉取会话列表为空
root_cause: 旧版套餐未开通云端会话功能，鸿蒙SDK需要开通云端会话才能拉取会话列表
solution: 需要单独申请开通云端会话功能，无需升级套餐。开通后即可正常使用getConversationList()拉取会话列表。
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# 鸿蒙SDK拉取会话列表为空

## 问题描述

在HarmonyOS中使用ConversationRepo.getConversationList()拉取最近会话列表返回数据为空

## 问题背景

- 使用的是旧版套餐
- 将appkey填入demo测试也出现相同情况

## 根因分析

旧版套餐未开通云端会话功能，鸿蒙SDK需要开通云端会话才能拉取会话列表

## 解决方案

需要单独申请开通云端会话功能，无需升级套餐。开通后即可正常使用getConversationList()拉取会话列表。

## 标签

- 鸿蒙
- 会话列表
- 云端会话
- 套餐权限

## 客户

- FVIP-云信-上海麦色

## 会话日期

2025-02-12
