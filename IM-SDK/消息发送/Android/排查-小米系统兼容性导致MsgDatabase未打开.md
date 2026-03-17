---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: Android
title: 发送消息失败MsgDatabase is not opened
root_cause: 小米的新系统兼容性问题，会导致进程无法唤起
solution: 升级到10.9.62版本解决了这个问题，可以从V9版(9.19.4)直接升级到V10，接口不用变。
customers: ["数字传递"]
source: chat_history
tags: ["MsgDatabase", "登录失败", "小米兼容性", "进程唤起", "版本升级"]
created: 2026-02-06
updated: 2026-03-17
---

## 问题：Android 发送消息失败MsgDatabase is not opened

## 问题详情

**现象**：
用户16502在App启动后默认初始化IM SDK并登录，但发送IM消息失败，报错：MsgDatabase is not opened. Please login first! 该问题出现频率较高，用户重启后有发送成功的情况。

**环境信息**：
- SDK 版本：9.19.4
- 平台：Android

## 排查过程

1. 检查用户登录状态 → 发现登录可能失败
2. 拉取SDK日志分析 → 发现错误：start NimService error: java.lang.SecurityException: Unable to start service, process is bad

**关键发现**：小米新系统兼容性问题，会导致进程无法唤起

## 问题原因

小米的新系统兼容性问题，会导致进程无法唤起

## 解决方案

升级到10.9.62版本解决了这个问题，可以从V9版(9.19.4)直接升级到V10，接口不用变。

## 其他触发场景
