---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: 通用
title: 服务端发送自定义消息含换行符导致客户端JSON解析失败
root_cause: 手动拼接JSON字符串时，换行符\r\n经SDK传输后被转换成实际换行符，导致最终JSON结构被破坏解析失败
solution: 使用JSON.stringify()方法正确序列化消息内容，避免手动字符串拼接；SDK侧换行符传输问题有待SDK团队进一步研究修复
customers: ["台州浩瀚网络"]
source: chat_history
tags: ["换行符","JSON解析","自定义消息","content为null","\\r\\n"]
created: 2025-08-28
updated: 2026-03-26
---

## 问题：通用 服务端发送自定义消息含换行符导致客户端JSON解析失败

## 问题详情

**现象**：
服务端发送自定义消息（type:100），当job_content字段包含换行符(\\r\\n)时，客户端收到消息的content字段为null，JSON解析失败。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 服务端排查：确认服务端attach内容正常 → 排除服务端问题
2. 客户端排查：SDK日志显示JSON.parse失败 → 定位解析层
3. 对比测试：直接用系统JSON.stringify方法完全正常 → 排除JSON问题本身
4. 根因：使用JSON.stringify时\\r\\n会被SDK处理成实际\\r\\n导致JSON格式破坏 → 根因确认

**关键发现**：手动拼接JSON字符串时，换行符\\r\\n经SDK传输后被转换成实际换行符，导致最终JSON结构被破坏解析失败

## 问题原因

手动拼接JSON字符串时，换行符\\r\\n经SDK传输后被转换成实际换行符，导致最终JSON结构被破坏解析失败。

## 解决方案

使用JSON.stringify()方法正确序列化消息内容，避免手动字符串拼接；SDK侧换行符传输问题有待SDK团队进一步研究修复。

## 其他触发场景

（合并时在此处追加）
