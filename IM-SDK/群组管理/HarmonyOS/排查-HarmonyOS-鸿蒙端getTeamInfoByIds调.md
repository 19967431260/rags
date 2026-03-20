---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 群组管理
platform: HarmonyOS
title: 鸿蒙端getTeamInfoByIds调用异常
root_cause: 登录异常导致
solution: 检查登录状态，确保IM登录成功后再调用群组相关API
customers: ["智己"]
source: chat_history
tags: ["鸿蒙", "getTeamInfoByIds", "V2NIMError", "登录异常", "queryMyTeamsCount"]
created: 2025-11-04
updated: 2026-03-20
---

## 问题：HarmonyOS 鸿蒙端getTeamInfoByIds调用异常

## 问题详情

**现象**：
鸿蒙平台调用NIMInitManager.getInstance().nim.teamService?.getTeamInfoByIds([teamId], V2NIMTeamType.V2NIM_TEAM_TYPE_NORMAL)后异常，返回错误{"name":"V2NIMError","code":0,"desc":"unknown error","detail":{"reason":"queryMyTeamsCount","rawError":{}}}。

## 排查过程

1. 要求客户提供SDK日志文件
2. 客户通过鸿蒙开发工具Device File Browser获取日志路径：data/app/el2/100/base/包名/haps/nim/cache/nim_log/
**关键发现**：日志显示登录异常，初始化登录都没有完成

## 问题原因

登录异常导致

## 解决方案

检查登录状态，确保IM登录成功后再调用群组相关API

## 其他触发场景

