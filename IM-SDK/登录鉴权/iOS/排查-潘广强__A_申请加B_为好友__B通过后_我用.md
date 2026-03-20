---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: iOS
title: @潘广强  A 申请加B 为好友， B通过后，我用
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: @潘广强  A 申请加B 为好友， B通过后，我用服务端接口nimserver/msg/sendMsg.action 给B发送 提示消息： “您已同意对方的好友申请” ， 同时给A发送“对方已同意您的
customers: ["VIP云信-江苏爱驿站信息科技有限公司"]
source: chat_history
tags: ["登录", "消息", "回调", "视频"]
created: 2025-01-02
updated: 2026-03-20
---

## 问题：iOS @潘广强  A 申请加B 为好友， B通过后，我用

## 问题详情

@潘广强  A 申请加B 为好友， B通过后，我用服务端接口nimserver/msg/sendMsg.action 给B发送 提示消息： “您已同意对方的好友申请” ， 同时给A发送“对方已同意您的好友申请”，现在A和B的界面上都有两个文案，怎么做到B看到的是“您已同意对方的好友申请” ，A看到的只是“对方已同意您的好友申请”？；https://ysf.nosdn.127.net/5d9b49c2ebe24649be450e94d03c8217.jpg?download=5d9b49c2ebe24649be450e94d03c8217.jpg；您现在的文案不是本地插入的，是依赖服务器发送的展

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

@潘广强  A 申请加B 为好友， B通过后，我用服务端接口nimserver/msg/sendMsg.action 给B发送 提示消息： “您已同意对方的好友申请” ， 同时给A发送“对方已同意您的

## 其他触发场景
