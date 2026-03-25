---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 群成员管理
platform: Electron
title: getTeamMemberList查询群成员信息不完整
root_cause: beta版node-nim本地数据库缓存损坏导致群成员数据异常
solution: 清理本地缓存目录%LocalAppData%\NIM后重新登录，或升级到正式版node-nim
customers: ["深圳联友"]
source: chat_history
tags: ["getTeamMemberList", "群成员", "beta", "缓存", "Electron"]
created: 2025-04-01
updated: 2025-04-30
---

## 问题：getTeamMemberList查询群成员信息不完整

## 问题详情

**现象**：
调用teamService.getTeamMemberList查询群成员，只能查到自己一个人，其他成员查不到

**环境信息**：
- 平台：Electron

## 排查过程

1. 检查入参 → 确认teamId和查询参数正确
2. 对比测试 → 正式版node-nim查询正常，beta版有问题
3. 检查本地缓存 → 发现beta版本地数据库可能损坏
4. 清理缓存验证 → 清理%LocalAppData%\NIM目录后恢复正常

## 根因分析

beta版node-nim本地数据库缓存损坏导致群成员数据异常

## 解决方案

清理本地缓存目录%LocalAppData%\NIM后重新登录，或升级到正式版node-nim

## 其他触发场景

（无）
