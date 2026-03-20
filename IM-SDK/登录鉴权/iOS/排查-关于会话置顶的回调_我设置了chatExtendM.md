---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: iOS
title: 关于会话置顶的回调，我设置了chatExtendM
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: 关于会话置顶的回调，我设置了chatExtendManager
customers: ["VIP云信-北京云动（会小二）"]
source: chat_history
tags: ["token", "登录", "回调", "群组"]
created: 2025-01-20
updated: 2026-03-20
---

## 问题：iOS 关于会话置顶的回调，我设置了chatExtendM

## 问题详情

关于会话置顶的回调，我设置了chatExtendManager；[[NIMSDK sharedSDK].chatExtendManager addDelegate:self];；然后把配置也开了；[[NIMSDKConfig sharedConfig] setShouldSyncStickTopSessionInfos:YES];；登录后，onNotifySyncStickTopSessions是正常回调的，能拿到我之前置顶的会话

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

关于会话置顶的回调，我设置了chatExtendManager

## 其他触发场景
