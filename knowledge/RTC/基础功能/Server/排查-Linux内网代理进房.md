---
track_type: 排查类
sub_type: 功能实现咨询
product: RTC
feature: 房间管理
platform: Server
title: Linux SDK内网代理进房问题
root_cause: "网络配置问题"
solution: "检查代理配置和网络连通性"
customers: ["云信"]
source: chat_history
tags: ["SDK"]
created: 2025-06-10
updated: 2025-03-23
---

## 问题：Linux SDK内网代理进房问题

## 问题详情

**现象**：
Linux SDK在内网走代理进云端房间有问题。

**环境信息**：
- 平台：Server/Linux
- 场景：内网走代理

## 排查过程

1. 查看日志 → 分析连接问题
2. 对比配置 → 与南京跑通的配置对比
3. 检查代理 → 确认代理服务器配置

## 问题原因

内网代理配置或网络连通性问题

## 解决方案

1. 对比南京跑通的配置
2. 检查代理服务器地址和端口
3. 确认网络策略是否开放相应端口

## 其他触发场景

