---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息发送
platform: iOS
title: iOS用户发不出消息问题排查
root_cause: wifi网络限制导致连接问题，同时存在重复login问题
solution: 建议升级到SDK 9.20.12版本，对已知耗时问题做了处理
customers:
  - 海岛游
source: chat_history
tags:
  - 消息发送
  - iOS
  - 网络限制
  - SDK升级
created: '2025-06-19'
updated: '2025-03-23'
---

## 问题：iOS iOS用户发不出消息问题排查

## 问题详情

**现象**：
用户反馈经常发不出消息，问题出现时间6月18日23:29，土耳其地区用户

**排查过程**：

1. 检查服务器日志 → 发消息时IM可能掉线
2. 发现问题 → 重复login问题仍存在
3. 分析日志 → wifi网络有限制，获取历史记录和发消息都没成功
4. 建议升级 → 9.19.x做过连接优化

**关键发现**：wifi网络限制导致连接问题，同时存在重复login问题

## 问题原因

wifi网络限制导致连接问题，同时存在重复login问题

## 解决方案

建议升级到SDK 9.20.12版本，对已知耗时问题做了处理
