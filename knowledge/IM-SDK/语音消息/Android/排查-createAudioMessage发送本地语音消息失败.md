---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 语音消息
platform: Android
title: createAudioMessage发送本地语音消息失败
root_cause: 部分低版本安卓设备需要显式申请文件读取权限才能访问内部存储的语音文件。
solution: 添加文件读取权限申请，确保应用有权限访问语音文件。
customers: ['上海移云信息科技有限公司']
source: chat_history
tags: ['语音消息', 'createAudioMessage', '权限', 'Android', '内部存储']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：Android createAudioMessage发送本地语音消息失败

## 问题详情

**现象**：
客户使用createAudioMessage方法发送本地语音消息，部分手机发送失败。语音文件存放在内部存储目录。

## 排查过程

1. 客户怀疑是文件存储目录问题
2. 分析日志未发现发送失败记录
3. 客户自行添加文件读取权限后问题解决

## 问题原因

部分低版本安卓设备需要显式申请文件读取权限才能访问内部存储的语音文件。

## 解决方案

添加文件读取权限申请，确保应用有权限访问语音文件。

## 其他触发场景

（合并时在此处追加）
