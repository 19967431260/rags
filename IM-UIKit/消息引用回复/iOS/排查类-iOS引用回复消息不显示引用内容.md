---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 消息引用回复
platform: iOS
title: iOS引用回复消息不显示引用内容
root_cause: loadMoreWithMessage方法中group.leave()在loadReply的回调中执行，导致在特定情况下引用消息加载逻辑未正确执行。
solution: 修改loadMoreWithMessage方法，将group.leave()从loadReply回调中移出，与loadReply调用平级放置，确保引用消息加载完成后再执行group.leave()。
customers: ['东莞霖感科技有限公司']
source: chat_history
tags: ['iOS', 'UIKit', '引用回复', 'loadReply', 'P2PChatViewController']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：iOS引用回复消息不显示引用内容

## 问题详情

**现象**：
在继承P2PChatViewController后，使用引用回复功能时，消息发送成功但引用的消息内容没有在下方显示。问题出现在自定义聊天详情页中。

## 排查过程

1. 客户反馈引用回复后消息不显示引用内容 → 技术支持建议用demo复现
2. 客户使用自定义P2PChatViewController → 技术支持提供loadMoreWithMessage方法修改方案
3. 发现group.leave()在loadReply回调中执行导致问题 → 将group.leave()移出到与loadReply平级位置

## 问题原因

loadMoreWithMessage方法中group.leave()在loadReply的回调中执行，导致在特定情况下引用消息加载逻辑未正确执行。

## 解决方案

修改loadMoreWithMessage方法，将group.leave()从loadReply回调中移出，与loadReply调用平级放置，确保引用消息加载完成后再执行group.leave()。

## 其他触发场景

（合并时在此处追加）
