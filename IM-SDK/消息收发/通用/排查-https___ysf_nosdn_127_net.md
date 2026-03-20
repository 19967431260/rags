---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: 通用
title: https://ysf.nosdn.127.net
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: 双方并不是好友关系吧？非好友是需要收到对方发来的消息或者主动去服务端拉取一遍信息才会同步下来的 否则按照默认逻辑展示，可能会展示accid
customers: ["VIP云信-成都职工投资集团有限公司"]
source: chat_history
tags: ["404", "消息", "云信", "技术支持", "历史会话"]
created: 2025-01-14
updated: 2026-03-20
---

## 问题：通用 https://ysf.nosdn.127.net

## 问题详情

https://ysf.nosdn.127.net/0b850f9dd478462296444bc22ae4a1aa.jpg?download=0b850f9dd478462296444bc22ae4a1aa.jpg；@姚肖；https://ysf.nosdn.127.net/13d4f0659c404b39bc6a2f6e4fcff720.jpg?download=13d4f0659c404b39bc6a2f6e4fcff720.jpg；这个第一次进入列表页面的时候，显示是会话ID 吗？；进入会话页面，再返回就正常显示会话昵称了

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

双方并不是好友关系吧？非好友是需要收到对方发来的消息或者主动去服务端拉取一遍信息才会同步下来的 否则按照默认逻辑展示，可能会展示accid

## 其他触发场景
