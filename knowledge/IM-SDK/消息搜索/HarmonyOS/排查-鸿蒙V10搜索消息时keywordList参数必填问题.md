---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "消息搜索"
platform: "HarmonyOS"
title: "鸿蒙V10搜索消息时keywordList参数必填问题"
root_cause: "V2NIMMessageSearchExParams参数校验规则：当消息发送者以及消息类型均未指定时，必须设置关键字列表；否则，关键字列表可以为空"
solution: "如需按群id和时间搜索而不指定keyword，需要同时指定senderAccountIds、messageTypes或messageSubtypes中的至少一个参数，否则必须传入keywordList"
customers: ["好未来-yach"]
source: "chat_history"
tags: ["鸿蒙", "searchCloudMessagesEx", "searchLocalMessages", "keywordList", "参数异常"]
created: "2025-09-02"
updated: "2026-03-20"
---

## 问题：HarmonyOS 鸿蒙V10搜索消息时keywordList参数必填问题

## 问题详情

**现象**：
鸿蒙版本10.9.10使用searchCloudMessagesEx或searchLocalMessages搜索聊天记录时，如果只传入群id和时间筛选，不传keywordList会报参数异常。错误提示：When 'senderAccountIds' and 'messageTypes' and 'messageSubtypes' are not specified(undefined/[]), 'keywordList' is required.

## 排查过程

1. 客户反馈keyword传空时搜索异常
2. 确认客户调用的是searchCloudMessagesEx还是searchLocalMessages
3. 客户确认只传入群id和时间，不传keywordList
4. 查看错误日志发现当senderAccountIds、messageTypes、messageSubtypes都未指定时，keywordList是必填参数

## 问题原因

V2NIMMessageSearchExParams参数校验规则：当消息发送者以及消息类型均未指定时，必须设置关键字列表；否则，关键字列表可以为空

## 解决方案

如需按群id和时间搜索而不指定keyword，需要同时指定senderAccountIds、messageTypes或messageSubtypes中的至少一个参数，否则必须传入keywordList

## 其他触发场景
