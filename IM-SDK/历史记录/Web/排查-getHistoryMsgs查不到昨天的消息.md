---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 历史记录
platform: Web
title: getHistoryMsgs查不到昨天的消息
root_cause: getHistoryMsgs接口的beginTime参数传值错误，传入了订单创建时间而非历史查询起始时间，导致只能查到当天消息
solution: getHistoryMsgs接口的beginTime参数如果不确定传什么值，可以传0，这样可以查询到所有历史消息
customers: ["创业慧康科技股份", "杭州东方网升"]
source: chat_history
tags: ["getHistoryMsgs", "beginTime", "历史消息", "参数错误", "Web"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Web getHistoryMsgs查不到昨天的消息

## 问题详情

**现象**：
医生端在微信H5中调用getHistoryMsgs接口查询历史消息时，只能看到当天的消息，看不到昨天发送的消息。accid为a7fce810b92d4b459d949e5e8ae8140d，使用Web SDK。

## 排查过程

1. 检查accid a7fce810b92d4b459d949e5e8ae8140d的消息记录 → 确认该账号看不到2026-02-02 08:37:45之前的消息
2. 检查getHistoryMsgs接口调用参数 → 发现beginTime传值为1769992642000（对应2026-02-02 08:37:22）

**关键发现**：beginTime参数传的是订单开始时间orderDetail.createDt，导致只能查到该时间点之后的消息，无法查询昨天的历史消息

## 问题原因

getHistoryMsgs接口的beginTime参数传值错误，传入了订单创建时间而非历史查询起始时间，导致只能查到当天消息

## 解决方案

getHistoryMsgs接口的beginTime参数如果不确定传什么值，可以传0，这样可以查询到所有历史消息

## 其他触发场景

（暂无）
