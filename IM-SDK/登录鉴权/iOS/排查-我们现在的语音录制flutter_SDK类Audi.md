---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: iOS
title: 我们现在的语音录制flutter SDK类Audi
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: 我们现在每次启动APP时都调用了login登录接口。如果之前已经登录了，是不是启动的时候的不用调用？
customers: ["VIP云信-北京百骏天成科技有限公司"]
source: chat_history
tags: ["登录", "云信", "技术支持", "历史会话"]
created: 2025-01-02
updated: 2026-03-20
---

## 问题：iOS 我们现在的语音录制flutter SDK类Audi

## 问题详情

我们现在的语音录制flutter SDK类AudioService，是支持暂停和继续录制的吧。 @石志诚；稍等；https://ysf.nosdn.127.net/2e8b875a5b904cf1831b440bb7dbe275.jpg?download=2e8b875a5b904cf1831b440bb7dbe275.jpg；好的~；@一即一切 不支持的，我看了下原生 SDK 也只有开始和结束或者取消

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

我们现在每次启动APP时都调用了login登录接口。如果之前已经登录了，是不是启动的时候的不用调用？

## 其他触发场景
