---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 登录认证
platform: Flutter
title: 频繁刷新token导致重连失败消息历史丢失
root_cause: 静态token本不会过期，但业务层每次启动都刷新token，导致重连时认证失败，关闭本地数据库
solution: 去掉定时刷新token和首页刷新token的逻辑，只在用户修改密码或登录失败302时才刷新token。云信静态token永久有效，无需频繁刷新
customers: ["东莞市仁众丽科技有限公司"]
source: chat_history
tags: ["Flutter", "token刷新", "重连失败", "消息历史", "静态token", "动态token"]
created: 2025-05-29
updated: 2025-03-20
---

## 问题：Flutter 频繁刷新token导致重连失败消息历史丢失

## 问题详情

**现象**：
用户进入聊天界面时消息历史不显示。排查发现客户端在启动时频繁刷新token，导致重连过程中触发PWD_ERROR状态，关闭本地数据库。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：Flutter

## 排查过程

1. 检查日志 → 发现重连过程中更换了密码(token)
2. 确认token刷新逻辑 → 客户端每次打开APP都刷新token
3. 分析影响 → 刷新token后重连失败，需要重新手动登录
4. 提供解决方案 → 建议去掉不必要的token刷新

## 问题原因

静态token本不会过期，但业务层每次启动都刷新token，导致重连时认证失败，关闭本地数据库

## 解决方案

去掉定时刷新token和首页刷新token的逻辑，只在用户修改密码或登录失败302时才刷新token。云信静态token永久有效，无需频繁刷新

## 其他触发场景

