---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 通知栏推送
platform: Android
title: 小米推送channel info不匹配错误27001
root_cause: 小米推送的channel配置不匹配，需要在控制台配置默认channel或在发消息时通过payload指定
solution: 在控制台配置默认channel_id，或在发消息时通过payload指定channel_id。payload中的channel配置优先级高于控制台配置。
customers: ["福州市玄星网络科技有限公司"]
source: chat_history
tags: ["小米推送","27001","channel","配置错误"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：Android 小米推送channel info不匹配错误27001

## 问题详情

**现象**：
小米推送失败，错误码27001，错误信息"invalid channel info!"。客户在云信控制台配置了小米推送证书，但推送时返回channel相关信息不匹配。

## 排查过程

1. 检查推送日志 → 发现ErrorCode=27001: invalid channel info!
2. 检查控制台配置 → 发现客户配置了多个channel_id
3. 检查推送参数 → payload中的channel配置优先级更高

**关键发现**：channel配置不匹配导致推送失败

## 问题原因

小米推送的channel配置不匹配，需要在控制台配置默认channel或在发消息时通过payload指定

## 解决方案

在控制台配置默认channel_id，或在发消息时通过payload指定channel_id。payload中的channel配置优先级高于控制台配置。

## 其他触发场景

