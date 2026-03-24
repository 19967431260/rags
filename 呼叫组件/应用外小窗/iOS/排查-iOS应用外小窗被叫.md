---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 应用外小窗
platform: iOS
title: iOS应用外小窗被叫方黑屏问题
root_cause: 被叫方获取uid逻辑错误，需要判断当前登录账号是否为被叫方accid
solution: 源码集成时，判断[[NECallEngine sharedInstance] getCallInfo].calleeInfo.accid是否为当前登录账号，是则截图使用callerInfo.uid，否则使用calleeInfo.uid
customers: ["山东中时通"]
source: chat_history
tags: ["应用外小窗", "黑屏", "被叫方", "uid"]
created: 2025-02-11
updated: 2026-03-20
---

## 问题：iOS iOS应用外小窗被叫方黑屏问题

## 问题详情

**现象**：
客户配置应用外小窗功能后，呼叫方正常，被叫方小窗显示黑屏无画面。

## 排查过程

1. 确认demo可复现 → 问题存在
2. 分析代码逻辑 → 被叫方uid获取逻辑有误
3. 修改判断逻辑 → 验证通过

## 问题原因

被叫方获取uid逻辑错误，需要判断当前登录账号是否为被叫方accid

## 解决方案

源码集成时，判断[[NECallEngine sharedInstance] getCallInfo].calleeInfo.accid是否为当前登录账号，是则截图使用callerInfo.uid，否则使用calleeInfo.uid

## 其他触发场景

