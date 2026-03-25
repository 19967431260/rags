---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "自定义通知"
platform: "Android"
title: "APP进入后台后收不到自定义系统通知"
root_cause: "Android系统对后台应用有严格的网络限制策略，应用进入后台后很快会被系统限制网络访问，导致与服务器连接断开，无法接收自定义通知。这是系统行为，无法通过应用层设置完全避免。"
solution: "后台运行时以厂商离线推送为主。应用进入后台后被系统限制网络访问是系统行为，无法通过代码设置避免。建议在后台场景下依赖离线推送机制来接收消息通知。"
customers: ["FVIP云信-大连誉实"]
source: "chat_history"
tags: ["自定义通知", "observeCustomNotification", "后台", "掉线", "网络限制", "Android"]
created: "2025-09-28"
updated: "2026-03-20"
---

## 问题：Android APP进入后台后收不到自定义系统通知

## 问题详情

**现象**：
客户反馈Android端注册observeCustomNotification接收自定义系统通知，当APP进入后台时observer没有被调用。

## 排查过程

1. 客户提供logcat日志显示java.io.IOException: Software caused connection abort
2. 检查日志发现应用退后台后被系统限制网络访问导致掉线
3. 客户反馈插上USB充电时能正常收到，进一步验证是后台网络限制问题

## 问题原因

Android系统对后台应用有严格的网络限制策略，应用进入后台后很快会被系统限制网络访问，导致与服务器连接断开，无法接收自定义通知。这是系统行为，无法通过应用层设置完全避免。

## 解决方案

后台运行时以厂商离线推送为主。应用进入后台后被系统限制网络访问是系统行为，无法通过代码设置避免。建议在后台场景下依赖离线推送机制来接收消息通知。

## 其他触发场景
