---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话漫游
platform: HarmonyOS
title: 鸿蒙端getConversationListByIds查询不到历史会话
root_cause: 没有开通漫游，无法生成会话。大于30天没有产生过数据的老会话，换一台没有登录过的设备，这个会话就不会生成
solution: 需要开通漫游功能，或理解漫游策略限制。参考文档：https://faq.yunxin.163.com/#KB0014
customers: ["好未来-yach"]
source: chat_history
tags: ["会话漫游","getConversationListByIds","鸿蒙","历史会话"]
created: 2025-02-08
updated: 2025-03-20
---

## 问题：HarmonyOS 鸿蒙端getConversationListByIds查询不到历史会话

## 问题详情

**现象**：
使用getConversationListByIds接口查询，有些会话查不到数据。Android和鸿蒙使用同一个账号，很早的群Android能看到，鸿蒙看不到。

## 排查过程

1. 确认使用的是localConversationService → 确认接口正确
2. 分析发现没有漫游无法生成会话 → 定位问题

**关键发现**：没有开通漫游，无法生成会话

## 问题原因

没有开通漫游，无法生成会话。大于30天没有产生过数据的老会话，换一台没有登录过的设备，这个会话就不会生成。

## 解决方案

需要开通漫游功能，或理解漫游策略限制。参考文档：https://faq.yunxin.163.com/#KB0014

## 其他触发场景

