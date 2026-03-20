---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 推送通知
platform: 小程序
title: 微信小程序发送这个消息后：netcall.c
root_cause: ""
solution: "这是一条引用/回复消息：
“徐秀滨:
clientJoin事件正常，netcall.switchMode切到1时（关闭摄像头）
clientLeave事件异常，基本没收到过”
------
@徐秀滨 "
customers: ["FVIP云信-智业互联健康科技"]
source: chat_history
tags: ["云信", "SDK", "技术支持"]
created: 2025-01-06
updated: 2026-03-20
---

## 问题：小程序 微信小程序发送这个消息后：netcall.c

## 问题详情

**现象**：
微信小程序发送这个消息后：netcall.control({
command: app.globalData.netcall.NETCALL_CONTROL_COMMAND_NOTIFY_VIDEO_OFF,
})
接收方经常性会接收不到
netcall.on('control', (data) => {})
这个有啥办法吗？

## 排查过程

1. 根据会话信息确认问题触发路径并复核关键配置。

## 问题原因

会话中未提供更细根因。

## 解决方案

这是一条引用/回复消息：
“徐秀滨:
clientJoin事件正常，netcall.switchMode切到1时（关闭摄像头）
clientLeave事件异常，基本没收到过”
------
@徐秀滨 
