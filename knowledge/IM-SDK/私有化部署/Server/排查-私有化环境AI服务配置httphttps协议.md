---
track_type: "排查类"
sub_type: "配置开通咨询"
product: "IM-SDK"
feature: "私有化部署"
platform: "Server"
title: "私有化环境AI服务配置http/https协议"
root_cause: "AI服务实际使用http协议，与文档中的https描述不一致"
solution: "AI服务私有化配置使用http协议而非https，地址格式：http://ip:port"
customers: ["申万宏源"]
source: "chat_history"
tags: ["IM-SDK", "私有化", "AI服务", "http", "https", "配置"]
created: "2025-09-01"
updated: "2026-03-20"
---

## 问题：Server 私有化环境AI服务配置http/https协议

## 问题详情

**现象**：
私有化部署中AI服务地址配置问题，客户配置https无法访问，改为http后可以访问。

## 排查过程

1. 客户反馈配置https://172.22.93.161:86无法访问
2. 改为http://172.22.93.161:86后可以访问
3. 但文档中写的是https
**关键发现**：中台之前邮件发的是https，实际确认后是http

## 问题原因

AI服务实际使用http协议，与文档中的https描述不一致

## 解决方案

AI服务私有化配置使用http协议而非https，地址格式：http://ip:port

## 其他触发场景
