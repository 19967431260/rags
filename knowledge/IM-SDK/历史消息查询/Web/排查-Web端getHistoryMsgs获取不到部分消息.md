---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 历史消息查询
platform: Web
title: Web端getHistoryMsgs获取不到部分消息
root_cause: 客户使用错误的accid查询历史消息，导致查不到数据。需要使用消息的发送方或接收方accid查询。
solution: 确保使用正确的accid（消息的发送方或接收方）调用getHistoryMsgs查询历史消息；需要在onsyncdone回调之后调用getHistoryMsgs
customers: ['北京十月逸栈']
source: chat_history
tags: ['getHistoryMsgs', '历史消息', 'Web', '查询不到', 'onsyncdone']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：Web Web端getHistoryMsgs获取不到部分消息

## 问题详情

**现象**：
客户反馈Web端调用nim.getHistoryMsgs获取历史消息时，部分消息能查到，部分查不到，但服务端API能查到。

## 排查过程

1. 确认服务端是否有数据 → 服务端API能查到，说明消息存在
2. 检查调用时机 → 发现日志提示'Please call getHistoryMsgs after onsyncdone callback'
3. 检查参数设置 → 确认reverse参数未传
4. 调试定位 → 发现客户查询时使用的accid不是消息的发送方或接收方

## 问题原因

客户使用错误的accid查询历史消息，导致查不到数据。需要使用消息的发送方或接收方accid查询。

## 解决方案

确保使用正确的accid（消息的发送方或接收方）调用getHistoryMsgs查询历史消息；需要在onsyncdone回调之后调用getHistoryMsgs

## 其他触发场景

（合并时在此处追加）
