---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 服务端API
platform: Server
title: RTC房间API域名与普通API不同
root_cause: RTC房间的API域名与普通IM API域名不同，需要使用rtc-api.yunxinapi.com
solution: RTC相关API使用独立域名：rtc-api.yunxinapi.com。
customers: ["VIP云信-长沙点盐科技有限公司-dx"]
source: chat_history
tags: ["RTC", "API域名", "404", "房间查询"]
created: 2025-11-10
updated: 2026-03-20
---

## 问题：Server RTC房间API域名与普通API不同

## 问题详情

**现象**：
查询已结束房间成员时返回404错误，使用的是普通API域名。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认trace-id → c224e553c87a4e28931a0e39dc912336
2. 检查API域名 → 使用普通API域名
**关键发现**：RTC房间API需要使用独立域名

**关键发现**：

## 问题原因

RTC房间的API域名与普通IM API域名不同，需要使用rtc-api.yunxinapi.com

## 解决方案

RTC相关API使用独立域名：rtc-api.yunxinapi.com。

## 其他触发场景

