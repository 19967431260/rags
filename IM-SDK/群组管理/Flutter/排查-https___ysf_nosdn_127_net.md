---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: Flutter
title: https://ysf.nosdn.127.net
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: 需要基于这个发送者ID手动查询用户资料再展示
customers: ["VIP云信-广西源龙网络科技有限公司-dx"]
source: chat_history
tags: ["云信", "技术支持", "历史会话"]
created: 2025-01-14
updated: 2026-03-20
---

## 问题：Flutter https://ysf.nosdn.127.net

## 问题详情

https://ysf.nosdn.127.net/1802a235f56549d980195bfe671be2c4.jpg?download=1802a235f56549d980195bfe671be2c4.jpg；@Adiljan 这里沟通哈；需要基于这个发送者ID手动查询用户资料再展示；https://ysf.nosdn.127.net/2abd78d7c532414e8ea9918253a5b198.jpg?download=2abd78d7c532414e8ea9918253a5b198.jpg；如果取巧一点，可以发送的时候把发送方自己的用户资料设置到扩展字段里，接收方用扩展信息去获

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

需要基于这个发送者ID手动查询用户资料再展示

## 其他触发场景
