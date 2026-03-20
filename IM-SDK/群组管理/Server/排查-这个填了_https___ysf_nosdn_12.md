---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: Server
title: 这个填了 https://ysf.nosdn.12
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: @麻世庆 @云信技术值班三号 请教一下问题：https://doc.yunxin.163.com/messaging/server-apis/DQ2NTg4ODE?platform=server#返回
customers: ["VIP云信-极之客-dx"]
source: chat_history
tags: ["消息", "回调", "云信", "技术支持", "历史会话"]
created: 2025-01-22
updated: 2026-03-20
---

## 问题：Server 这个填了 https://ysf.nosdn.12

## 问题详情

这个填了；https://ysf.nosdn.127.net/5f7071b2f5884021a107fa35cec42d43.jpg?download=5f7071b2f5884021a107fa35cec42d43.jpg；@麻世庆 @云信技术值班三号 请教一下问题：https://doc.yunxin.163.com/messaging/server-apis/DQ2NTg4ODE?platform=server#返回参数；这个msgid跟抄送收到的msgIdServer是同一个东西吗；您好，是的 这个就是服务端的消息id，是服务端存储消息的主键

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

@麻世庆 @云信技术值班三号 请教一下问题：https://doc.yunxin.163.com/messaging/server-apis/DQ2NTg4ODE?platform=server#返回

## 其他触发场景
