---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 房间生命周期
platform: Android
title: NERoom收到END_OF_RTC房间结束回调
root_cause: 主播操作关闭直播间触发RTC房间关闭
solution: END_OF_RTC表示RTC房间结束，需要检查业务层是否在主播端调用了关闭直播间接口
customers: ["高途预见塔塔项目"]
source: chat_history
tags: ["NERoom", "Android", "END_OF_RTC", "房间结束", "onRoomEnded"]
created: 2025-02-12
updated: 2026-03-20
---

## 问题：Android NERoom收到END_OF_RTC房间结束回调

## 问题详情

**现象**：
主播端放着不动，过一会儿收到onRoomEnded事件，reason为END_OF_RTC，后台也收到关播抄送。

## 排查过程

1. 客户反馈主播端无故收到onRoomEnded回调
2. 收集live_id和咨询师云信侧用户id
3. 查询RTC房间上报，发现被踢出房间
4. 进一步分析是主播关闭直播间触发

## 问题原因

主播操作关闭直播间触发RTC房间关闭

## 解决方案

END_OF_RTC表示RTC房间结束，需要检查业务层是否在主播端调用了关闭直播间接口

## 其他触发场景
- [Android] NERoom收到END_OF_RTC房间结束回调，来源：['高途预见塔塔项目']，2026-03-20
- [Android] NERoom收到END_OF_RTC房间结束回调，来源：['高途预见塔塔项目']，2026-03-20

