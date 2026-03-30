---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话列表
platform: 安卓
title: V10安卓会话列表name显示为会话ID
root_cause: 本地数据库没有对应的用户资料，SDK默认展示对方账号。需要在合适的时机主动查询用户资料。
solution: 在会话列表展示前主动批量查询用户资料，参考文档：https://doc.yunxin.163.com/messaging2/guide/zYwMzU1NTI?platform=client#获取用户资料
customers: ["杭州跨客技术服务有限公司"]
source: chat_history
tags: ["会话列表", "name显示", "用户资料", "安卓", "V10"]
created: 2025-05-20
updated: 2025-03-20
---

## 问题：安卓 V10安卓会话列表name显示为会话ID

## 问题详情

**现象**：
从V9升级到V10后，安卓端会话列表中会话name显示为会话ID，而iOS端显示正常。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：安卓

## 排查过程

1. 客户反馈安卓会话name显示异常 → 技术支持解释昵称由SDK本地组装
2. 确认本地db没有用户资料时默认展示对方账号 → 建议主动批量查询用户资料
3. iOS也复现相同问题，确认是查询时机问题

## 问题原因

本地数据库没有对应的用户资料，SDK默认展示对方账号。需要在合适的时机主动查询用户资料。

## 解决方案

在会话列表展示前主动批量查询用户资料，参考文档：https://doc.yunxin.163.com/messaging2/guide/zYwMzU1NTI?platform=client#获取用户资料

## 其他触发场景

