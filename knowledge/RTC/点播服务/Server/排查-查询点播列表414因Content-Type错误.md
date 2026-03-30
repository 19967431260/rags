---
track_type: 排查类
sub_type: 测试问题
product: RTC
feature: 点播服务
platform: Server
title: 查询点播列表414因Content-Type错误
root_cause: 请求头 Content-Type 不符合点播接口要求，导致接口未按 JSON 方式解析请求。
solution: 调用点播查询接口时将 Content-Type 设置为 application/json，再按 JSON 格式传参即可。
customers: ["备胎网络"]
source: chat_history
tags: ["414", "channelId is empty", "Content-Type", "application/json", "VOD"]
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Server 查询点播列表414因Content-Type错误

## 问题详情

**现象**：
客户调用点播视频查询接口 `https://vcloud.163.com/app/vod/video/list` 时返回 `code=414`、`desc="channelId is empty!"`，但入参中并未要求必须传 channelId。

**相关日志**：
- 返回结果：`{"code":414,"desc":"channelId is empty!"}`

## 排查过程

1. 客户提供查询接口地址、请求参数和 414 报错信息。
2. 技术支持确认具体 appkey 以便排查。
3. 客户后续自查确认问题已恢复，并定位到请求头 Content-Type 配置有误。

**关键发现**：点播接口要求使用 `application/json` 请求头，否则可能返回误导性的 414 错误。

## 问题原因

请求头 Content-Type 不符合点播接口要求，导致接口未按 JSON 方式解析请求。

## 解决方案

调用点播查询接口时将 Content-Type 设置为 `application/json`，再按 JSON 格式传参即可。

## 其他触发场景

