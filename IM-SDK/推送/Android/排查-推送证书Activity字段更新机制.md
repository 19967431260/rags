---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: Android
title: 推送证书Activity字段更新机制
root_cause: 控制台证书更新逻辑不会同步更新activity字段，需要删除并重新上传证书才能生效。
solution: 推送证书中的Activity字段如需更新，需要删除并重新上传证书，仅修改不会同步更新。建议控制台增加字段说明提示。
customers: ['臻络']
source: chat_history
tags: ['推送证书', 'Activity', 'badge', '更新机制']
created: 2025-02-25
updated: 2026-03-23
---

## 问题：Android 推送证书Activity字段更新机制

## 问题详情

**现象**：
客户删除控制台推送证书中的Activity字段后，推送中仍包含该字段，咨询更新机制。

**环境信息**：
- 平台：Android
- 产品：IM-SDK

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认控制台已删除Activity → 已删除
2. 检查推送记录 → 仍包含badgeClass
3. 确认更新逻辑 → 证书更新不会同步删除activity字段
4. 提供解决方案 → 删除并重新上传证书

## 问题原因

控制台证书更新逻辑不会同步更新activity字段，需要删除并重新上传证书才能生效。

## 解决方案

推送证书中的Activity字段如需更新，需要删除并重新上传证书，仅修改不会同步更新。建议控制台增加字段说明提示。

## 其他触发场景

（合并时在此处追加：`- [Android] 推送证书Activity字段更新机制，来源：['臻络']，2026-03-23`）
