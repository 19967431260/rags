---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 快捷评论
platform: Android
title: queryQuickComment回调param为空问题
root_cause: queryQuickComment传入的msgList为null时，callback中param会返回空
solution: 调用queryQuickComment时确保msgList参数不为null，或对返回的param进行判空处理
customers: ["VIP云信-广州春洣贸易有限公司"]
source: chat_history
tags: ["快捷评论", "queryQuickComment", "param为空", "Android"]
created: 2025-02-18
updated: 2026-03-20
---

## 问题：Android queryQuickComment回调param为空问题

## 问题详情

**现象**：
Android端使用queryQuickComment获取快捷评论时，线上监测到callback中param偶尔为空，导致Index 0 out of bounds异常。

## 排查过程

1. 正常情况下param有数据
2. 线上偶现param为空的情况
3. 排查发现当msgList为null时会出现此问题

## 问题原因

queryQuickComment传入的msgList为null时，callback中param会返回空

## 解决方案

调用queryQuickComment时确保msgList参数不为null，或对返回的param进行判空处理

## 其他触发场景
- [Android] queryQuickComment回调param为空问题，来源：['VIP云信-广州春洣贸易有限公司']，2026-03-20

