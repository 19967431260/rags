---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群组管理
platform: Web
title: getTeamInfoByIds查询群详情无扩展字段
root_cause: getTeamInfoByIds查询的是群资料，不是会话对象
solution: getTeamInfoByIds查询的是群资料，不会返回会话的serverExtension扩展字段。会话列表和群详情是两个不同的对象。
customers: ["海康华安"]
source: chat_history
tags: ["群组", "getTeamInfoByIds", "serverExtension", "Web", "会话"]
created: 2025-02-27
updated: 2026-03-20
---

## 问题：Web getTeamInfoByIds查询群详情无扩展字段

## 问题详情

**现象**：
客户反馈会话列表中有serverExtension字段，但用群id查群详情时没有这个字段。

## 排查过程

1. 客户提供查询代码
2. 技术支持指出查的是群资料不是会话对象
3. 确认getTeamInfoByIds返回的是群资料，不会返回会话的扩展字段

## 问题原因

getTeamInfoByIds查询的是群资料，不是会话对象

## 解决方案

getTeamInfoByIds查询的是群资料，不会返回会话的serverExtension扩展字段。会话列表和群详情是两个不同的对象。

## 其他触发场景
- [Web] getTeamInfoByIds查询群详情无扩展字段，来源：['海康华安']，2026-03-20

