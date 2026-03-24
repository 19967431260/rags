---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 断网处理
platform: HarmonyOS
title: 鸿蒙端断网下getMessageList卡住导致崩溃
root_cause: 断网状态下im未登录，getTeamMembers在断网情况下获取本地数据要到10.9.0版本才行
solution: getTeamMembers在断网情况下获取本地数据功能将在10.9.0版本支持，预计3月底发布
customers: ["好未来-yach"]
source: chat_history
tags: ["断网","getMessageList","崩溃","190002","10.9.0"]
created: 2025-02-17
updated: 2025-03-20
---

## 问题：HarmonyOS 鸿蒙端断网下getMessageList卡住导致崩溃

## 问题详情

**现象**：
断网下getMessageList接口会卡住，过段时间app崩溃。单聊是好的，群有问题。

## 排查过程

1. 内部测试未复现 → 排除通用问题
2. 客户demo测试正常 → 进一步确认
3. 发现TeamMemberCache getTeamMembers error code = 190002报错 → 发现关键错误
4. 确认是im未登录导致 → 定位根因

**关键发现**：断网状态下im未登录，getTeamMembers在断网情况下获取本地数据要到10.9.0版本才行

## 问题原因

断网状态下im未登录，getTeamMembers在断网情况下获取本地数据要到10.9.0版本才行。

## 解决方案

getTeamMembers在断网情况下获取本地数据功能将在10.9.0版本支持，预计3月底发布。

## 其他触发场景

