---
track_type: 咨询类
sub_type: 接口用法咨询
product: IM-SDK
feature: 消息管理
platform: Flutter
title: Flutter V10更新消息本地扩展
root_cause: V10 Flutter版本目前不支持更新消息的serverExtension和attachment，只能更新本地扩展localExtension。
solution: 使用updateMessageLocalExtension方法更新消息的本地扩展。注意：1. localExtension只能本地读取，不会同步给其他端；2. 如需获取会话最后一条消息的localExtension，需调用getMessageListByIds通过messageClientId查询完整消息对象；3. serverExtension和attachment更新功能春节后排期支持。
customers: ['海南无限链科技有限公司']
source: chat_history
tags: ['Flutter', 'V10', '本地扩展', 'localExtension', '更新消息']
created: 2025-01-23
updated: 2026-03-23
---

## 问题：Flutter V10更新消息本地扩展

## 问题详情

**现象**：
需要更新已有消息的本地扩展字段（如红包消息状态变更），并能查询更新后的数据。

## 排查过程

1. 客户尝试使用updateMessageLocalExtension方法；2. 发现更新后数据未生效；3. 确认V10 Flutter版本暂不支持更新serverExtension。

## 问题原因

V10 Flutter版本目前不支持更新消息的serverExtension和attachment，只能更新本地扩展localExtension。

## 解决方案

使用updateMessageLocalExtension方法更新消息的本地扩展。注意：1. localExtension只能本地读取，不会同步给其他端；2. 如需获取会话最后一条消息的localExtension，需调用getMessageListByIds通过messageClientId查询完整消息对象；3. serverExtension和attachment更新功能春节后排期支持。

## 其他触发场景

（合并时在此处追加）
