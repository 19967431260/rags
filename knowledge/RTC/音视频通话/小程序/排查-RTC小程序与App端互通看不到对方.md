---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频通话
platform: 小程序
title: RTC小程序与App端互通看不到对方
root_cause: 小程序端使用了demo的获取逻辑，传入111后demo根据业务逻辑获取了demo定义的channelname，而非使用传入值。
solution: 按照SDK底层逻辑处理，不要依赖demo的获取逻辑。客户端加入房间时的channelname应使用服务端创建房间时传入的channelName字符串。
customers: ['良医健康医疗科技(辽宁)有限公司']
source: chat_history
tags: ['RTC', '小程序', 'App', '房间', 'channelname', '互通']
created: 2024-12-31
updated: 2026-03-23
---

## 问题：小程序 RTC小程序与App端互通看不到对方

## 问题详情

**现象**：
App端与小程序端使用相同appkey和房间号进入房间后，互相看不到对方。

## 排查过程

1. 检查房间人数 → 后台显示只有Android端加入房间
2. 确认小程序端加入的房间号 → 客户确认都是111
3. 检查小程序console日志 → 发现channelname不是111
4. 分析原因 → 客户使用demo的获取逻辑，channelname被demo业务逻辑修改

## 问题原因

小程序端使用了demo的获取逻辑，传入111后demo根据业务逻辑获取了demo定义的channelname，而非使用传入值。

## 解决方案

按照SDK底层逻辑处理，不要依赖demo的获取逻辑。客户端加入房间时的channelname应使用服务端创建房间时传入的channelName字符串。

## 其他触发场景

（合并时在此处追加）
