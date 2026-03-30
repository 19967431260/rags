---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录
platform: 通用
title: IM自动登录失败报错NIMLoginStepLoginFailed/LinkFailed
root_cause: 根据登录日志查询，未发现登录失败的记录，用户实际仍有成功登录的情况。
solution: 通过后台登录登出数据上报查询（2-2表示登录，2-4表示离线），确认用户登录状态正常，未发现失败记录。
customers: ["HIYAK GLOBAL LIMITED"]
source: chat_history
tags: ["NIMLoginStepLoginFailed", "NIMLoginStepLinkFailed", "登录失败", "自动登录", "登录日志"]
created: 2025-06-23
updated: 2026-03-23
---

## 问题：通用 IM自动登录失败报错NIMLoginStepLoginFailed/LinkFailed

## 问题详情

**现象**：
客户反馈在特定时间段内，大面积用户出现IM自动登录失败，报错NIMLoginStepLoginFailed、NIMLoginStepLinkFailed。客户提供两个用户accid供排查。

**环境信息**：
（从会话提取，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 查询用户登录日志 → 发现用户10:57仍有成功登录记录
2. 下发日志任务等待用户上传日志
3. 查询登录登出数据上报 → 2-2表示登录，2-4表示离线
4. 查询全部登录记录 → 未发现非200的失败记录

**关键发现**：根据登录日志查询，未发现登录失败的记录，用户实际仍有成功登录的情况。

## 问题原因

根据登录日志查询，未发现登录失败的记录，用户实际仍有成功登录的情况。

## 解决方案

通过后台登录登出数据上报查询（2-2表示登录，2-4表示离线），确认用户登录状态正常，未发现失败记录。

## 其他触发场景

