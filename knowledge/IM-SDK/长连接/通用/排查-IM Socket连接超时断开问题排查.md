---
track_type: 排查类
sub_type: 客户环境问题
product: IM-SDK
feature: 长连接
platform: 通用
title: IM Socket连接超时断开问题排查
root_cause: 特定时间点网络环境不稳定导致IM Socket连接超时
solution: 建议抓包给网管分析网络环境；监听连接断开事件做相应处理
customers: ['SI云信-顺丰科技-小哥在线项目']
source: chat_history
tags: ['长连接', '超时', '断开连接', '网络问题']
created: 2025-01-22
updated: 2026-03-23
---

## 问题：通用 IM Socket连接超时断开问题排查

## 问题详情

**现象**：
客户反馈有台机器每天早上第一次登录都会出现连接断开，发消息超时。

## 排查过程

1. 客户反馈早上第一次登录必现断开
2. 查看日志发现是网络请求超时导致的断开
3. 错误码disconnected，error_code: 4
4. 建议抓包分析网络环境
5. 确认时间点固定，可能是网络环境问题

## 问题原因

特定时间点网络环境不稳定导致IM Socket连接超时

## 解决方案

建议抓包给网管分析网络环境；监听连接断开事件做相应处理

## 其他触发场景

（合并时在此处追加）
