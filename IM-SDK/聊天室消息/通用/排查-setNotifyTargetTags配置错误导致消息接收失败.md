---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室消息
platform: 通用
title: setNotifyTargetTags配置错误导致消息接收失败
root_cause: setNotifyTargetTags使用AND逻辑组合多个tag条件，且正则匹配写法不正确，导致消息通知目标过滤失败
solution: setNotifyTargetTags改为单一tag匹配，如{"tag": "66477345.*", "matchType": "regex"}或{"tag": "66477345"}；全部匹配可不设置notifyTargetTags
customers:
  - 湖南腾速科技
source: chat_history
tags:
  - IM
  - 聊天室
  - setNotifyTargetTags
  - 消息通知
  - tag匹配
created: '2025-06-28'
updated: '2025-03-23'
---

## 问题：通用 setNotifyTargetTags配置错误导致消息接收失败

## 问题详情

**现象**：
聊天室中某用户发送的消息其他端接收不到，刷新后可以收到。客户使用setNotifyTargetTags设置消息通知目标标签。

**排查过程**：

1. 客户反馈特定用户消息接收不到
2. 查询登录参数 → 发现接收方tags为[66477345,494900,...]
3. 查询发送方配置 → setNotifyTargetTags使用默认AND逻辑
4. 发现发送方设置{"tag": ".*", "matchType": "regex"}后接收方仍收不到
5. 判断正则匹配逻辑问题

**关键发现**：setNotifyTargetTags使用AND逻辑组合多个tag条件，且正则匹配写法不正确，导致消息通知目标过滤失败

## 问题原因

setNotifyTargetTags使用AND逻辑组合多个tag条件，且正则匹配写法不正确，导致消息通知目标过滤失败

## 解决方案

setNotifyTargetTags改为单一tag匹配，如{"tag": "66477345.*", "matchType": "regex"}或{"tag": "66477345"}；全部匹配可不设置notifyTargetTags
