---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息
platform: Android
title: Android导出消息报错-104因上传token过期
root_cause: 用户很久未上传文件时，本地缓存的上传token已过期（半年有效期），导致-104错误。
solution: 1. SDK会在发现token过期后自动更新一批新token\n2. 遇到-104错误后，再次调用exportAllMessage接口即可成功\n3. 建议在应用层遇到-104时自动重试一次
customers: ["广州心晴"]
source: chat_history
tags: ["exportAllMessage","-104","token过期","MsgExportProcessor","Android"]
created: 2025-08-11
updated: 2026-03-26
---

## 问题：Android Android导出消息报错-104因上传token过期

## 问题详情

**现象**：
客户Android端调用exportAllMessage接口导出聊天记录时，MsgExportProcessor中抛出自定义异常后收到-104错误。另外用户第一次上传失败、第二次成功。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户在MsgExportProcessor中抛异常计算上传大小导致接口报-102
2. 但最终出现-104错误 → token过期
3. 客服确认：用户很久没有上传过文件时，缓存在本地的上传token会过期（一般半年），再次调用即可成功

**关键发现**：用户很久未上传文件时，本地缓存的上传token已过期（半年有效期），导致-104错误。

## 问题原因

用户很久未上传文件时，本地缓存的上传token已过期（半年有效期），导致-104错误。

## 解决方案

1. SDK会在发现token过期后自动更新一批新token
2. 遇到-104错误后，再次调用exportAllMessage接口即可成功
3. 建议在应用层遇到-104时自动重试一次

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
