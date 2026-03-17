---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: Web
title: Web SDK离线收到消息后会话updateTime未更新
root_cause: ""
solution: 实例化时db需要开启。更新会话走的是另外一个地方，需要有db::putSession开头的日志。代码逻辑中两种情况都会更新updateTime，如果再出现需要完整日志分析
customers: ["时间在线"]
source: chat_history
tags: ["Web SDK","updateTime","会话列表","离线消息","debug","db"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：Web Web SDK离线收到消息后会话updateTime未更新

## 问题详情

**现象**：
Web SDK v9.20.12版本，在离线情况下收到对方消息，最近会话updateTime显示的还是昨天，但最新消息的time是今天的。在新的浏览器或同源下，实例化时debug要开启过一次，会话才会去更新updateTime。

**环境信息**：
- SDK 版本：v9.20.12
- 平台：Web

## 排查过程

1. 检查完整console日志 → 日志只有片段
2. 检查本地设备时间 → 正常
3. 检查db::putSession日志 → 实例化时db关闭了
4. 实例化时db开启后问题解决

**关键发现**：实例化时db开启后问题解决，但在新浏览器没打开过debug时updateTime不更新

## 问题原因

根因未完全明确，与实例化时db状态相关

## 解决方案

实例化时db需要开启。更新会话走的是另外一个地方，需要有db::putSession开头的日志。代码逻辑中两种情况都会更新updateTime，如果再出现需要完整日志分析。

## 其他触发场景

（暂无）
