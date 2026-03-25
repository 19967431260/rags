---
track_type: "排查类"
sub_type: "集成类"
product: "RTC"
feature: "getChannelInfo"
platform: "Web"
title: "Web端getChannelInfo返回非JSON数据导致解析错误"
root_cause: "getChannelInfo服务端返回的数据非JSON格式"
solution: "查看浏览器开发者工具网络选项卡中getChannelInfo接口的实际返回数据，确认返回格式问题"
customers: ["政采云"]
source: "chat_history"
tags: ["getChannelInfo", "JSON解析", "Web", "数据格式"]
created: "2025-09-18"
updated: "2026-03-20"
---

## 问题：Web Web端getChannelInfo返回非JSON数据导致解析错误

## 问题详情

**现象**：
localhost启动后报错，错误提示解析的数据非JSON格式

## 排查过程

1. 查看错误截图 → 确认错误为数据解析失败
2. 分析原因 → 服务端返回的数据非JSON格式
**关键发现**：getChannelInfo接口返回数据格式异常

## 问题原因

getChannelInfo服务端返回的数据非JSON格式

## 解决方案

查看浏览器开发者工具网络选项卡中getChannelInfo接口的实际返回数据，确认返回格式问题

## 其他触发场景
