---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: iOS
title: iOS消息接收回调未触发
root_cause: 可能与七鱼SDK冲突或代理设置问题
solution: 建议先不要重装拉取完整日志分析，检查代理设置和七鱼SDK版本
customers: ["知聊"]
source: chat_history
tags: ["iOS", "收不到消息", "onRecvMessages", "七鱼", "代理"]
created: 2025-11-06
updated: 2026-03-20
---

## 问题：iOS iOS消息接收回调未触发

## 问题详情

**现象**：
用户0026842174在20:50到22点期间一直收不到消息，onRecvMessages未触发，但服务器视角看登录成功。

## 排查过程

1. 查询服务器登录记录
2. 检查消息发送记录
3. 分析本地日志
**关键发现**：服务器日志显示登录成功，消息已下发且已读上报，但客户埋点显示onRecv未触发

## 问题原因

可能与七鱼SDK冲突或代理设置问题

## 解决方案

建议先不要重装拉取完整日志分析，检查代理设置和七鱼SDK版本

## 其他触发场景

