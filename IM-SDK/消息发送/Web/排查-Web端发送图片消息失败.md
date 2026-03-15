---
track_type: 排查类
sub_type: 客户开发能力
product: IM-SDK
feature: 消息发送
platform: Web
title: Web端发送图片消息失败
root_cause: 图片上传配置不正确或上传接口调用失败
solution: 检查图片上传配置，确保nosAccess配置正确。参考文档配置图片上传参数。
customers: ["云信-北京中科金财科技股份有限公司"]
source: chat_history
tags: ['Web', '图片消息', '上传失败', 'nosAccess']
created: 2026-02-13
updated: 2026-03-15
---

## 问题：Web Web端发送图片消息失败

## 问题详情

**现象**：
Web端发送图片消息时失败，无法正常发送。

## 排查过程

1. 检查图片上传 → 失败
2. 检查错误信息 → 上传接口报错
**关键发现**：图片上传配置问题

## 问题原因

图片上传配置不正确或上传接口调用失败

## 解决方案

检查图片上传配置，确保nosAccess配置正确。参考文档配置图片上传参数。
