---
track_type: 排查类
sub_type: 客户环境问题
product: RTC
feature: 基础功能
platform: Server
title: QUIC代理连接被拒绝
root_cause: "quic_proxy_server连接被拒绝"
solution: "检查代理服务器配置和网络连通性"
customers: ["云信"]
source: chat_history
tags: ["消息","168217"]
created: 2025-06-16
updated: 2025-03-23
---

## 问题：QUIC代理连接被拒绝

## 问题详情

**现象**：
数字人服务器到192.168.0.46的UDP7070探测是通的，但QUIC连接被拒绝。

**环境信息**：
- 平台：Server
- 代理地址：192.168.0.46:7070

## 排查过程

1. 网络探测 → UDP 7070端口通
2. 查看日志 → QUIC_MSG_REJECT
3. 分析原因 → 连接被服务端拒绝

**关键日志**：
```
[06-16 10:07:17.131] WSQuicClient open: uri->wss://192.168.0.46:7070/
[06-16 10:07:21.192] QUIC_MSG_REJECT
[06-16 10:07:21.193] on_conn_closed
```

## 问题原因

quic_proxy_server连接被拒绝，可能是代理服务器配置问题或内外网代理不通。

## 解决方案

1. 检查代理服务器日志
2. 确认内外网代理配置
3. 尝试不设置quic_proxy测试

## 其他触发场景

