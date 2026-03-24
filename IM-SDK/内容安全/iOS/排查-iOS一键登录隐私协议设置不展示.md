---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 内容安全
platform: iOS
title: iOS一键登录隐私协议设置不展示
root_cause: appPrivacyText需要包含相关关键字才能生效
solution: appPrivacyText参数需要包含相关关键字才能生效，修改传参内容确保包含必要关键字
customers: ['流体网络']
source: chat_history
tags: ['一键登录', 'iOS', '隐私协议', 'appPrivacyText']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：iOS iOS一键登录隐私协议设置不展示

## 问题详情

**现象**：
iOS一键登录底部的同意协议，按文档传参后协议内容不会展示出来

## 排查过程

1. 客户反馈设置model.appPrivacyText后协议不展示
2. 技术支持要求提供appPrivacyText内容
3. 客户修改appPrivacyText后可以正常展示

## 问题原因

appPrivacyText需要包含相关关键字才能生效

## 解决方案

appPrivacyText参数需要包含相关关键字才能生效，修改传参内容确保包含必要关键字

## 其他触发场景

（合并时在此处追加）
