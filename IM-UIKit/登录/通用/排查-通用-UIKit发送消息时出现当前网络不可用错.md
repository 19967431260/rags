---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 登录
platform: 通用
title: UIKit发送消息时出现当前网络不可用错误
root_cause: 发送消息时登录协议未完成或网络断开
solution: 在onLoginFailed回调中处理错误，根据错误码判断是否展示弹窗。UIKit统一错误处理位置可自定义。
customers: ["东莞市面具网络科技有限公司"]
source: chat_history
tags: ["UIKit", "登录失败", "网络不可用", "onLoginFailed"]
created: 2025-11-05
updated: 2026-03-20
---

## 问题：通用 UIKit发送消息时出现当前网络不可用错误

## 问题详情

**现象**：
客户使用UIKit 10.6.1发消息时出现'当前网络不可用，请稍后重试'提示。

**排查过程**：
1. 确认错误发生在发送登录协议时网络断开
2. 判断为登录失败导致
3. 提供错误处理位置

## 问题原因

发送消息时登录协议未完成或网络断开

## 解决方案

在onLoginFailed回调中处理错误，根据错误码判断是否展示弹窗。UIKit统一错误处理位置可自定义。
