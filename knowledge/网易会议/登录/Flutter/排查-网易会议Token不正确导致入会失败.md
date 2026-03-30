---
track_type: 排查类
sub_type: 使用问题
product: 网易会议
feature: 登录
platform: Flutter
title: 网易会议Token不正确导致入会失败
root_cause: 进入会议时token不正确导致鉴权失败，并非真的超出设备限制。
solution: 检查token是否正确，确保登录成功后再入会。登录成功后后台不要刷新token，避免再次入会时报错。
customers: ['达济中道(沈阳)信息科技']
source: chat_history
tags: ['网易会议', 'Flutter', 'Token', '登录', '入会', '鉴权']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：Flutter 网易会议Token不正确导致入会失败

## 问题详情

**现象**：
相同账号在五个设备同时登录后会议进不去，提示报错。

## 排查过程

1. 确认报错信息 → 客户提供截图
2. 分析日志 → 发现loginByToken返回code:402, msg:Token不正确
3. 确认问题 → 登录时token不正确导致入会鉴权失败

## 问题原因

进入会议时token不正确导致鉴权失败，并非真的超出设备限制。

## 解决方案

检查token是否正确，确保登录成功后再入会。登录成功后后台不要刷新token，避免再次入会时报错。

## 其他触发场景

（合并时在此处追加）
