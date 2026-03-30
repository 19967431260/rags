---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Android
title: 被拉黑用户发送消息重启后状态异常
root_cause: 客户流程问题：本地插入的消息使用resend=true发送导致状态异常。正常流程应该是本地插入的消息要发送时重新构造新消息，或者不设置resend参数。
solution: 修改发送流程：1)先删除之前插入的本地消息，然后重新构造新消息发送 2)或者发送时resend不要设置或设置为false。sendMessage方法调用后本地会自动存储，与直接插入本地消息的策略不同。
customers: ["海岛游"]
source: chat_history
tags: ["IM-SDK", "Android", "7101", "消息发送", "resend", "拉黑"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：Android 被拉黑用户发送消息重启后状态异常

## 问题详情

**现象**：
用户5376被5377拉黑后发送文本消息（内容：12301，uuid:2e54d17429be47d3a66b97e2c991e621），发送时返回7101错误码状态为fail，但杀掉app重启后该消息状态变为success且serverId从0变为1770172093752（像时间戳）。发送流程：1)创建文本消息 2)保存到本地并显示 3)调用sendMessage(message, true)发送，resend设置为true。

**环境信息**：
- 平台：Android

## 排查过程

1. 检查日志 → 只找到发送失败记录，此时应该没有serverid
2. 通过SDK接口查历史记录打印消息 → 发现serverId异常为1770172093752
3. 分析流程 → 客户先插入本地消息，审核通过后用resend=true发送
4. 测试验证 → 正常流程下本地插入消息不应该用resend发送

**关键发现**：客户使用了不正确的消息发送流程，本地插入的消息不应该用resend方式发送

## 问题原因

客户流程问题：本地插入的消息使用resend=true发送导致状态异常。正常流程应该是本地插入的消息要发送时重新构造新消息，或者不设置resend参数。

## 解决方案

修改发送流程：1)先删除之前插入的本地消息，然后重新构造新消息发送 2)或者发送时resend不要设置或设置为false。sendMessage方法调用后本地会自动存储，与直接插入本地消息的策略不同。

## 其他触发场景
