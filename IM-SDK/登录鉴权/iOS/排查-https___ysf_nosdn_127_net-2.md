---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: iOS
title: https://ysf.nosdn.127.net
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: @严超 你好，我A邀请B加入群，B同意后会给A发一条私信，这条发给A的私信我想去掉应该怎么设置
customers: ["VIP云信-广州春洣贸易有限公司"]
source: chat_history
tags: ["500", "登录", "消息", "回调", "超时", "群组"]
created: 2025-01-15
updated: 2026-03-20
---

## 问题：iOS https://ysf.nosdn.127.net

## 问题详情

https://ysf.nosdn.127.net/dcacb6f359264a3c89adae2cd6844014.jpg?download=dcacb6f359264a3c89adae2cd6844014.jpg；@严超 你好，我A邀请B加入群，B同意后会给A发一条私信，这条发给A的私信我想去掉应该怎么设置；稍等，我这边看下；同意添加好友的请求后，我们只会下发系统通知，这条消息应该是你们自己发的。可以断点看下是不是有相关逻辑；不是添加好友，是邀请进群聊后会有一条私信

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

@严超 你好，我A邀请B加入群，B同意后会给A发一条私信，这条发给A的私信我想去掉应该怎么设置

## 其他触发场景
