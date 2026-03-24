---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 用户资料
platform: iOS
title: 群通知消息只显示accid不显示昵称
root_cause: 可能是本地缓存问题导致，具体原因需保留日志进一步分析
solution: 通知消息中只有用户云信账号，需要通过getUserListFromCloud查询云端用户资料获取昵称后展示。如遇到类似问题建议保留卸载重装前的日志。
customers: ['巽风科技']
source: chat_history
tags: ['群通知', '昵称', 'getUserListFromCloud', '用户资料']
created: 2025-01-21
updated: 2026-03-23
---

## 问题：iOS 群通知消息只显示accid不显示昵称

## 问题详情

**现象**：
客户反馈群通知消息中只显示用户accid，没有显示用户昵称。

## 排查过程

1. 确认源码中调用了getUserListFromCloud接口
2. 开发设备能正常显示昵称，测试设备不行
3. 建议导出日志排查
4. 测试反馈重装后恢复正常

## 问题原因

可能是本地缓存问题导致，具体原因需保留日志进一步分析

## 解决方案

通知消息中只有用户云信账号，需要通过getUserListFromCloud查询云端用户资料获取昵称后展示。如遇到类似问题建议保留卸载重装前的日志。

## 其他触发场景

（合并时在此处追加）
