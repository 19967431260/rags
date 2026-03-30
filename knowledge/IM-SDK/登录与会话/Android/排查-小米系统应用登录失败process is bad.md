---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录与会话
platform: Android
title: 小米系统应用登录失败process is bad
root_cause: 小米系统后台限制，应用被系统判定为"bad"进程导致服务无法启动。这是小米等特定厂商的系统限制问题。
solution: 在小米手机上设置：1. 设置自启动管理（允许应用自启动）；2. 关闭省电模式或设置为"无限制"。参考：https://blog.csdn.net/feitukejihui/article/details/103409376
customers: ["YOOY语音"]
source: chat_history
tags: ["小米","登录失败","process is bad","省电模式"]
created: 2025-08-13
updated: 2026-03-26
---

## 问题：Android 小米系统应用登录失败process is bad

## 问题详情

**现象**：
小米手机用户退到后台一段时间后无法连接云信SDK，一直处于登录中状态。错误信息：Unable to launch app com.nw.nawa.voice/10294 for service Intent { cmp=com.nw.nawa.voice/com.netease.nimlib.service.NimService }: process is bad。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 分析错误日志 → 小米系统限制了应用
2. 确认为小米系统特有的后台限制问题 → 系统限制
3. 提供解决方案参考文档 → 方案

**关键发现**：小米系统后台限制，应用被系统判定为"bad"进程导致服务无法启动。这是小米等特定厂商的系统限制问题。

## 问题原因

小米系统后台限制，应用被系统判定为"bad"进程导致服务无法启动。这是小米等特定厂商的系统限制问题。

## 解决方案

在小米手机上设置：1. 设置自启动管理（允许应用自启动）；2. 关闭省电模式或设置为"无限制"。参考：https://blog.csdn.net/feitukejihui/article/details/103409376

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
