---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话管理
platform: Uniapp
title: getHistoryMsgs查询不到历史消息
root_cause: getHistoryMsgs接口的to参数应传入accid，客户错误地传入了session。
solution: getHistoryMsgs的to参数直接写accid，不要写session。
customers: ['北京新流通信息科技有限公司']
source: chat_history
tags: ['getHistoryMsgs', '历史消息', '查询', '参数错误']
created: 2025-01-16
updated: 2026-03-23
---

## 问题：Uniapp getHistoryMsgs查询不到历史消息

## 问题详情

**现象**：
客户调用getHistoryMsgs查询历史消息无返回。

## 排查过程

1. 检查回调执行状态，发现回调未触发；2. 建议直接在控制台执行测试代码；3. 发现to参数错误，传的是session而非accid；4. 修正参数后查询成功。

## 问题原因

getHistoryMsgs接口的to参数应传入accid，客户错误地传入了session。

## 解决方案

getHistoryMsgs的to参数直接写accid，不要写session。

## 其他触发场景

（合并时在此处追加）
