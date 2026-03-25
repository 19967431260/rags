---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "离线推送"
platform: "Android"
title: "OPPO公信通道超限需申请私信通道"
root_cause: "OPPO推送公信通道有数量限制，超量后消息无法下发。"
solution: "1. 申请OPPO私信通道
2. 在云信控制台配置channelId（私信通道ID）
3. 或者在发送消息时通过客户端控制对应的channelId"
customers: ["FVIP云信-深圳富旅奇缘"]
source: "chat_history"
tags: ["OPPO", "离线推送", "公信", "私信通道", "channelId", "超限"]
created: "2025-09-11"
updated: "2026-03-20"
---

## 问题：Android OPPO公信通道超限需申请私信通道

## 问题详情

**现象**：
OPPO推送发送成功但用户收不到，排查工具显示公信超量。

## 排查过程

1. 查询云信推送记录显示给OPPO推送成功
2. 使用OPPO排查工具检查，显示设备上线但无推送数据
3. 反馈给OPPO客服确认是公信超了
4. 申请私信通道解决

## 问题原因

OPPO推送公信通道有数量限制，超量后消息无法下发。

## 解决方案

1. 申请OPPO私信通道
2. 在云信控制台配置channelId（私信通道ID）
3. 或者在发送消息时通过客户端控制对应的channelId

## 其他触发场景
