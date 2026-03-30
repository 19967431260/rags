---
track_type: "排查类"
sub_type: "集成类"
product: "IM-SDK"
feature: "账号管理"
platform: "服务端"
title: "海外appkey调用OpenAPI创建账号报错"
root_cause: "海外appkey需要使用海外专属域名调用API"
solution: "海外appkey改用海外对应域名：https://doc.yunxin.163.com/Overseas/guide/DgyODU1ODI"
customers: ["广州浪花"]
source: "chat_history"
tags: ["海外", "appkey", "OpenAPI", "创建账号", "域名"]
created: "2025-09-23"
updated: "2026-03-20"
---

## 问题：服务端 海外appkey调用OpenAPI创建账号报错

## 问题详情

**现象**：
测试环境使用openapi创建账号时报错，客户使用的是海外appkey。

## 排查过程

1. 确认appkey为海外版本
2. 需使用海外对应的域名调用API

## 问题原因

海外appkey需要使用海外专属域名调用API

## 解决方案

海外appkey改用海外对应域名：https://doc.yunxin.163.com/Overseas/guide/DgyODU1ODI

## 其他触发场景
