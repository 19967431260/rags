---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: iOS
title: 咱们音视频通话有flutter版吗
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: 没有的，可以用信令来实现呼叫邀请传递房间号的逻辑
customers: ["VIP云信-北京未来星图"]
source: chat_history
tags: ["token", "消息", "视频"]
created: 2025-01-13
updated: 2026-03-20
---

## 问题：iOS 咱们音视频通话有flutter版吗

## 问题详情

咱们音视频通话有flutter版吗；有的，https://doc.yunxin.163.com/nertc/guide?platform=flutter；好的；这个能跟IM 一起使用 不冲突哈；不冲突

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

没有的，可以用信令来实现呼叫邀请传递房间号的逻辑

## 其他触发场景
