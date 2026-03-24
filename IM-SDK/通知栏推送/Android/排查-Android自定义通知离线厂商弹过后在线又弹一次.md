---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 通知栏推送
platform: Android
title: Android自定义通知离线厂商弹过后在线又弹一次
root_cause: 离线消息通过厂商通道已弹过一次通知，App在线后SDK会再次触发observeCustomNotification回调，导致业务层再次弹通知。
solution: 在observeCustomNotification回调中增加时间戳判断：若消息时间戳早于App进入前台或打开的时间，则判定为离线消息，不再弹出通知。
customers: ['VIP云信-臻络']
source: chat_history
tags: ['自定义通知', '离线推送', 'observeCustomNotification', '重复通知', 'Android']
created: 2025-01-15
updated: 2026-03-23
---

## 问题：Android Android自定义通知离线厂商弹过后在线又弹一次

## 问题详情

**现象**：
Android端使用自定义通知时，离线状态下消息通过厂商通道弹出系统通知，用户打开App在线后，又会收到云信的自定义通知回调，导致通知重复弹出。需要避免离线消息在在线状态下再次弹出通知。

## 排查过程



## 问题原因

离线消息通过厂商通道已弹过一次通知，App在线后SDK会再次触发observeCustomNotification回调，导致业务层再次弹通知。

## 解决方案

在observeCustomNotification回调中增加时间戳判断：若消息时间戳早于App进入前台或打开的时间，则判定为离线消息，不再弹出通知。

## 其他触发场景

（合并时在此处追加）
