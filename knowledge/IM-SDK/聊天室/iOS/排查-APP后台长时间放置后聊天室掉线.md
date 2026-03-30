---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 聊天室
platform: iOS
title: APP后台长时间放置后聊天室掉线
root_cause: 长时间在后台导致系统对APP限网，长连接断开。IM重连会一直尝试，聊天室最多重连20次后停止
solution: 业务层监听聊天室连接状态，掉线后手动重新进入聊天室。参考文档：https://doc.yunxin.163.com/messaging/guide/jQ1Mzk0OTA
customers: ["北京小刀万维"]
source: chat_history
tags: ["聊天室", "后台", "掉线", "重连", "iOS"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：APP后台长时间放置后聊天室掉线

## 问题详情

**现象**：
用户将APP长时间(约10分钟)放在后台后，聊天室自动退出，导致fetchChatroomMembers拉取不到成员。IM会自动重连但聊天室不会

**环境信息**：
- 平台：iOS

## 排查过程

1. 查询服务器日志 → 该时间点没有fetchChatroomMembers请求
2. 查询用户状态 → 该时间点用户已掉线
3. 查询后续登录 → IM重新登录但聊天室未重新进入
4. 确认原因 → 长时间后台导致系统限网，长连接断开

## 根因分析

长时间在后台导致系统对APP限网，长连接断开。IM重连会一直尝试，聊天室最多重连20次后停止

## 解决方案

业务层监听聊天室连接状态，掉线后手动重新进入聊天室。参考文档：https://doc.yunxin.163.com/messaging/guide/jQ1Mzk0OTA

## 其他触发场景

（无）
