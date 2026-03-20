---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: iOS
title: https://ysf.nosdn.127.net
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: 有问题的设备上，是不是做了网络限制，截图中的好几个域名都请求超时。试试在无任何网络限制的环境，有没有这些超时报错。
customers: ["VIP-云信-杭州东方网升"]
source: chat_history
tags: ["登录", "消息", "超时"]
created: 2025-01-02
updated: 2026-03-20
---

## 问题：iOS https://ysf.nosdn.127.net

## 问题详情

https://ysf.nosdn.127.net/76c8c4d26f0141e89f0911a6e3345e9b.jpg?download=76c8c4d26f0141e89f0911a6e3345e9b.jpg；https://ysf.nosdn.127.net/a9631dde98334239ac89722942e910c7.jpg?download=a9631dde98334239ac89722942e910c7.jpg；最近有几家客户反馈 无法聊天 帮忙看下 连接都是超时的@网易云信-王硕；https://ysf.nosdn.127.net/8565e10843ed4d578c46

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

有问题的设备上，是不是做了网络限制，截图中的好几个域名都请求超时。试试在无任何网络限制的环境，有没有这些超时报错。

## 其他触发场景
