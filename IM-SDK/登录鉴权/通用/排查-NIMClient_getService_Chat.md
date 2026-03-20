---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: 通用
title: NIMClient.getService(Chat
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: @随心而动 那问题应该是当时没有调用接口查询公屏消息吧？日志看到9:24:57-59有3次pullMessageHistoryExType的接口调用，都是对聊天室5699863786的查询，这个和服务
customers: ["VIP云信-南宁音符科技有限公司"]
source: chat_history
tags: ["登录", "消息", "视频"]
created: 2025-01-16
updated: 2026-03-20
---

## 问题：通用 NIMClient.getService(Chat

## 问题详情

NIMClient.getService(ChatRoomService.class).；pullMessageHistoryExType(roomId,；@麻世庆 问下哟，这个是本地查询还是远程查询啊，最近有批量用户反馈涉及云信历史加载等很慢显示出来；https://ysf.nosdn.127.net/d604effd961d492cb217684507ba7492.mp4?download=d604effd961d492cb217684507ba7492.mp4；suid：68f8109a8664f1009946a35addb4be5c

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

@随心而动 那问题应该是当时没有调用接口查询公屏消息吧？日志看到9:24:57-59有3次pullMessageHistoryExType的接口调用，都是对聊天室5699863786的查询，这个和服务

## 其他触发场景
