---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 用户资料
platform: iOS
title: iOS会话列表userInfo偶现返回nil
root_cause: SDK更新用户资料的时机问题，本地用户资料可能未及时更新。
solution: 遍历会话列表之前先调用fetchUserInfos从远端拉取用户资料，避免更新时机问题。
customers: ['深圳岸涌']
source: chat_history
tags: ['iOS', 'userInfo', 'nil', '用户资料', '更新时机', 'fetchUserInfos']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：iOS iOS会话列表userInfo偶现返回nil

## 问题详情

**现象**：
客户在会话列表接口回调中，conversationList里面的userInfo偶现返回nil，导致过滤后整个会话列表为空。

## 排查过程

1. 客户反馈会话列表回调中userInfo偶现nil
2. 客户做了过滤处理，userInfo==nil时会剔除，可能导致会话列表为空
3. 技术支持解释是SDK更新用户资料的时机问题
4. 建议遍历之前拉取云端用户资料fetchUserInfos避免更新时机问题
5. 客户确认在回调处卡断点会必现此问题
6. 确认来新消息后断点查看会正常
7. 最终确认是更新时机问题，建议先拉取云端数据解决

## 问题原因

SDK更新用户资料的时机问题，本地用户资料可能未及时更新。

## 解决方案

遍历会话列表之前先调用fetchUserInfos从远端拉取用户资料，避免更新时机问题。

## 其他触发场景

（合并时在此处追加）
