---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 服务端API
platform: Server
title: 海外appkey调用国内域名返回403错误
root_cause: 海外appkey必须使用海外域名api-sg.yunxinapi.com，使用国内域名会返回403
solution: 海外appkey调用海外域名api-sg.yunxinapi.com，国内appkey调用api.yunxinapi.com。
customers: ["VIP云信-郑州晨宙信息科技有限公司"]
source: chat_history
tags: ["403", "海外域名", "api-sg", "区域限制"]
created: 2025-11-10
updated: 2026-03-20
---

## 问题：Server 海外appkey调用国内域名返回403错误

## 问题详情

**现象**：
调用注册接口时返回{"code":403,"desc":"forbidden in current region"}，使用的是国内域名api.yunxinapi.com。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认appkey类型 → 海外appkey
2. 检查请求域名 → 使用了国内域名
**关键发现**：海外appkey需要使用海外域名

**关键发现**：

## 问题原因

海外appkey必须使用海外域名api-sg.yunxinapi.com，使用国内域名会返回403

## 解决方案

海外appkey调用海外域名api-sg.yunxinapi.com，国内appkey调用api.yunxinapi.com。

## 其他触发场景

