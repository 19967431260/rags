---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: 服务端
title: 服务端发送自定义消息失败
root_cause: 自定义消息的attachment字段长度超过10240字节限制或为空
solution: 自定义消息的attachment字段需要在1-10240字节之间,检查并调整消息内容大小
customers: ["深圳市哈雷彗星科技有限公司"]
source: chat_history
tags: ["自定义消息", "attachment", "长度限制", "10240", "服务端发送"]
created: 2026-02-08
updated: 2026-03-17
---

## 问题：服务端 服务端发送自定义消息失败

## 问题详情

**现象**：
服务端发送消息给客户端,客户端上报的消息能收到,但服务端推送给客户端的消息没有收到。

**环境信息**：
- 时间段: 2月6号 22:48:26
- 消息trace.id: 5e39d34a1f0688c8eb9130c6ceb0e4e3

## 排查过程

1. 提供消息trace.id查询后端日志 → 发现消息发送失败

**关键发现**：错误信息显示 "attachment length must be between 1 and 10240"

## 问题原因

自定义消息的attachment字段长度超过10240字节限制或为空

## 解决方案

自定义消息的attachment字段需要在1-10240字节之间,检查并调整消息内容大小

## 其他触发场景

