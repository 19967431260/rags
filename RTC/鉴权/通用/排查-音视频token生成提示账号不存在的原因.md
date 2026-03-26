---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 鉴权
platform: 通用
title: 音视频token生成提示账号不存在的原因
root_cause: IM账号和音视频账号是独立的；音视频token生成只需accid，不需要提前注册IM账号；但accid必须已在IM服务端注册过才能正常使用
solution: IM账号需通过IM服务端API（doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server）提前注册，音视频token是基于已存在的accid生成的
customers: ["天一科技（甘肃）有限公司"]
source: chat_history
tags: ["token生成","账号不存在","RTC","音视频","accid"]
created: 2025-08-27
updated: 2026-03-26
---

## 问题：通用 音视频token生成提示账号不存在的原因

## 问题详情

**现象**：
客户生成音视频token后提示账号不存在（账号未注册）。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（无详细排查步骤，从会话提取）

**关键发现**：IM账号和音视频账号是独立的；音视频token生成只需accid，不需要提前注册IM账号；但accid必须已在IM服务端注册过才能正常使用

## 问题原因

IM账号和音视频账号是独立的；音视频token生成只需accid，不需要提前注册IM账号；但accid必须已在IM服务端注册过才能正常使用。

## 解决方案

IM账号需通过IM服务端API（doc.yunxin.163.com/messaging2/server-apis/TQyNjgyMzc?platform=server）提前注册，音视频token是基于已存在的accid生成的。

## 其他触发场景

（合并时在此处追加）
