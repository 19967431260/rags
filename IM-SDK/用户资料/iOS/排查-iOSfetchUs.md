---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 用户资料
platform: iOS
title: iOS fetchUserInfos返回空头像昵称
root_cause: 可能是用户资料同步时机问题，导致本地未取云端数据展示。
solution: 本地复现问题，在查询方法处断点查看SDK回调数据，确认用户资料同步时机。
customers: ["广州元气"]
source: chat_history
tags: ["iOS", "fetchUserInfos", "用户资料", "头像", "昵称", "同步"]
created: 2025-02-27
updated: 2026-03-20
---

## 问题：iOS iOS fetchUserInfos返回空头像昵称

## 问题详情

**现象**：
客户使用iOS SDK通过fetchUserInfos获取用户列表信息，返回的头像和昵称全是空的，但安卓正常。

## 排查过程

1. 客户反馈iOS获取用户资料为空，安卓正常
2. 服务端检查用户资料存在
3. 建议本地复现并断点查看SDK回调数据
4. 可能是用户资料同步时机问题

## 问题原因

可能是用户资料同步时机问题，导致本地未取云端数据展示。

## 解决方案

本地复现问题，在查询方法处断点查看SDK回调数据，确认用户资料同步时机。

## 其他触发场景
- [iOS] iOS fetchUserInfos返回空头像昵称，来源：['广州元气']，2026-03-20
- [iOS] iOS fetchUserInfos返回空头像昵称，来源：['广州元气']，2026-03-20

