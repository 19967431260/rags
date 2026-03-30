---
track_type: 咨询类
sub_type: 接口用法咨询
product: IM-SDK
feature: 消息管理
platform: 通用
title: 消息附件attachment与serverExtension区别
root_cause: 
solution: attachment是消息附件字段，仅图片、语音、视频、文件类型消息有该字段，长度上限4096字节。serverExtension是消息服务端扩展字段，必须为JSON格式，长度上限2048字节，多端同步。更新消息会把云端存储的内容修改并同步给消息相关的所有人。
customers: ['海南无限链科技有限公司']
source: chat_history
tags: ['attachment', 'serverExtension', '消息附件', '扩展字段', '区别']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：消息附件attachment与serverExtension区别

## 问题详情

**现象**：
咨询消息附件attachment和serverExtension扩展字段的区别及适用场景。

## 排查过程



## 问题原因



## 解决方案

attachment是消息附件字段，仅图片、语音、视频、文件类型消息有该字段，长度上限4096字节。serverExtension是消息服务端扩展字段，必须为JSON格式，长度上限2048字节，多端同步。更新消息会把云端存储的内容修改并同步给消息相关的所有人。

## 其他触发场景

（合并时在此处追加）
