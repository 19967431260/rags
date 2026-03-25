---
track_type: "排查类"
sub_type: "客户环境问题"
product: "IM-SDK"
feature: "服务端API"
platform: "Server"
title: "服务端调用API报UnknownHostException"
root_cause: "服务器DNS解析问题，解析不到云信域名IP地址"
solution: "使用dig api.netease.im多试几次，对比dig @8.8.8.8 api.netease.im检查本地DNS解析是否会有失败情况"
customers: ["北京医月科技"]
source: "chat_history"
tags: ["UnknownHostException", "DNS", "服务端", "API", "解析失败"]
created: "2025-09-01"
updated: "2026-03-20"
---

## 问题：Server 服务端调用API报UnknownHostException

## 问题详情

**现象**：
客户服务端多次调用接口报错UnknownHostException: api.netease.im，DNS解析不到域名IP地址。

## 排查过程

1. 客户反馈偶现UnknownHostException错误
2. 确认是服务器DNS解析问题
3. 建议检查local DNS解析情况，对比8.8.8.8解析结果

## 问题原因

服务器DNS解析问题，解析不到云信域名IP地址

## 解决方案

使用dig api.netease.im多试几次，对比dig @8.8.8.8 api.netease.im检查本地DNS解析是否会有失败情况

## 其他触发场景
