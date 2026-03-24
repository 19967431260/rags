---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 线程管理
platform: Android
title: 不断进出聊天室导致NIM线程持续增加不回收
root_cause: NIM-HT-RoomMess线程高可用导致的重名线程持续增加问题，NIM-HT-fcs_hand是融合存储模块初始化创建
solution: 优化方向：1、解决NIM-HT-RoomMess线程持续增加问题 2、减少初始化fcs带来的NIM-HT-fcs_hand线程数。fcs线程是Java通过高可用创建的，显示名字一样但功能不同，不会回收
customers: ["北京米连科技-伊对"]
source: chat_history
tags: ["线程","聊天室","NIM-HT-RoomMess","NIM-HT-fcs_hand","OOM"]
created: 2025-02-21
updated: 2025-03-20
---

## 问题：Android 不断进出聊天室导致NIM线程持续增加不回收

## 问题详情

**现象**：
不断进出不同的房间，NIM线程持续增加不回收。海外项目使用SDK 9.19.4版本，伊对使用8.9.133版本正常。

## 排查过程

1. 对比伊对和海外项目SDK版本差异 → 版本对比
2. 测试发现NIM-HT-RoomMess线程持续增加 → 定位问题线程
3. 确认NIM-HT-fcs_hand线程初始化就会创建，退出进入不会增加 → 排除fcs问题
4. 定位到高可用导致的重名线程问题 → 确认根因

**关键发现**：NIM-HT-RoomMess线程高可用导致的重名线程持续增加问题

## 问题原因

NIM-HT-RoomMess线程高可用导致的重名线程持续增加问题，NIM-HT-fcs_hand是融合存储模块初始化创建。

## 解决方案

优化方向：
1. 解决NIM-HT-RoomMess线程持续增加问题
2. 减少初始化fcs带来的NIM-HT-fcs_hand线程数

fcs线程是Java通过高可用创建的，显示名字一样但功能不同，不会回收。

## 其他触发场景

