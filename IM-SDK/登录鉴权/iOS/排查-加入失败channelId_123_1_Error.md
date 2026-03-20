---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录鉴权
platform: iOS
title: 加入失败channelId：123_1 Error
root_cause: 会话中表现为配置或接口使用不一致导致。
solution: @Dark 可以把nertc的日志发我们看下；初始化的时候设置下loglevel =info
customers: ["VIP云信-邯郸市趣网传媒技术有限公司"]
source: chat_history
tags: ["登录", "消息", "回调", "音频", "视频"]
created: 2025-01-10
updated: 2026-03-20
---

## 问题：iOS 加入失败channelId：123_1 Error

## 问题详情

加入失败channelId：123_1 Error Domain=NERtcRemoteErrorDomain Code=30103 "room not found" UserInfo={NSLocalizedDescription=room not found}；音视频加入房间偶尔会这样是什么问题啊；这是一条引用/回复消息：；“Dark:；加入失败channelId：123_1 Error Domain=NERtcRemoteErrorDomain Code=30103 "room not found" UserInfo={NSLocalizedDescription=room not fo

## 排查过程

1. 根据会话记录核对配置与日志；2. 对关键接口与参数进行逐项验证。

## 问题原因

会话中表现为配置或接口使用不一致导致。

## 解决方案

@Dark 可以把nertc的日志发我们看下；初始化的时候设置下loglevel =info

## 其他触发场景
