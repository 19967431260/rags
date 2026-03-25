---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组
platform: iOS
title: updateTeamInfo后getTeamInfo未及时同步
root_cause: 更新入库需要时间，立即查询可能读到旧数据
solution: 不要立即查询，可以通过onTeamInfoUpdated事件监听获取最新的team信息
customers: ["圆通"]
source: chat_history
tags: ["V10", "updateTeamInfo", "getTeamInfo", "同步"]
created: 2025-05-21
updated: 2025-03-20
---

## 问题：iOS updateTeamInfo后getTeamInfo未及时同步

## 问题详情

**现象**：
V10中调用updateTeamInfo更新群信息或拉人后，在成功回调里立即调用getTeamInfo，拿到的team信息没有及时同步更新，需要加延迟才能拿到新的。

## 排查过程

**关键发现**：更新入库需要时间，立即查询可能读到旧数据

## 问题原因

更新入库需要时间，立即查询可能读到旧数据

## 解决方案

不要立即查询，可以通过onTeamInfoUpdated事件监听获取最新的team信息
