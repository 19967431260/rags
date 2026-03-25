---
track_type: "排查类"
sub_type: "集成类"
product: "IM-SDK"
feature: "消息更新"
platform: "Web"
title: "私有化环境modifyMessage接口超时"
root_cause: "私有化环境未部署hbase，不支持消息更新功能"
solution: "需要更新私有化服务端版本，部署hbase以支持消息更新功能"
customers: ["圆通IM私有化"]
source: "chat_history"
tags: ["Web", "modifyMessage", "protocol timeout", "hbase", "私有化"]
created: "2025-09-04"
updated: "2026-03-20"
---

## 问题：Web 私有化环境modifyMessage接口超时

## 问题详情

**现象**：
Web端调用modifyMessage更新消息时返回protocol timeout错误（code: 192004），私有化环境。

## 排查过程

1. 客户反馈modifyMessage调用超时
2. 查看SDK日志发现v2MessageP2pModify协议包超时
3. 服务端排查确认消息更新依赖hbase
**关键发现**：私有化环境不支持消息更新功能，缺少hbase依赖

## 问题原因

私有化环境未部署hbase，不支持消息更新功能

## 解决方案

需要更新私有化服务端版本，部署hbase以支持消息更新功能

## 其他触发场景
