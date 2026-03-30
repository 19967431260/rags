---
track_type: 排查类
sub_type: 功能实现咨询
product: 网易会议
feature: 基础功能
platform: Server
title: 创建视频会议房间cid与回调channelId不一致
root_cause: 创建房间和加入房间使用的房间名(cname)不一致
solution: 确保创建房间和加入房间使用相同的房间名，cid是房间唯一标识，房间销毁后重新创建cid会变化
customers:
  - 政采云
source: chat_history
tags:
  - cid
  - channelId
  - 房间创建
  - 回调
  - cname
created: '2025-06-03'
updated: '2026-03-23'
---

## 问题：Server 创建视频会议房间cid与回调channelId不一致

## 问题详情

**现象**：
创建视频会议房间时返回的cid与回调时的channelId不一致

**环境信息**：
- 平台：Server
- 时间：2025-06-03

## 排查过程

1. 确认问题场景 → 房间内有2个人A,B，创建房间记录cid，B离开后再次进入，cid和回调channelId不一样
2. 分析时间线 → 确认房间未关闭时用户离开和重新进入
3. 检查房间名 → 发现创建房间用的房间名是65c2f8493afc8e81，客户端实际加入用的房间名是7205799027095371807
4. 定位问题 → 房间名不一致导致cid不一致

**关键发现**：创建和加入使用的房间名(cname)不一致，导致cid自然不一样

## 问题原因

创建房间和加入房间使用的房间名(cname)不一致，cid是基于房间名生成的唯一标识

## 解决方案

1. 确保创建房间和加入房间使用相同的房间名(cname)
2. 理解cid是房间的唯一标识，房间销毁后重新创建cid会变化
3. eventType5是用户离开房间，所有用户离开后房间销毁
4. 默认不需要创建房间，直接加入即可，房间不存在会自动创建

## 其他触发场景
