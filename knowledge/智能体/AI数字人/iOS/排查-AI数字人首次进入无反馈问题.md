---
track_type: 排查类
sub_type: 使用问题
product: 智能体
feature: AI数字人
platform: iOS
title: AI数字人首次进入无反馈问题
root_cause: 初始化之后太快调用login方法，导致AI用户信息未完全初始化，aiUserAccid为nil
solution: 方案1：设置NEAIUserManager.shared.setProvider后，监听NEAIUserManager.shared.addAIUserChangeListener的onAIUserChanged回调，触发后再给数字人发消息。方案2：避免初始化后立即调用login，确保AI用户管理器初始化完成。
customers: ["杭州暖音科技有限公司"]
source: chat_history
tags: ["AI数字人", "无反馈", "首次安装", "初始化", "aiUserAccid"]
created: 2025-06-18
updated: 2025-03-23
---

## 问题：iOS AI数字人首次进入无反馈问题

## 问题详情

**现象**：
客户反馈第一次安装app后直接走登录流程进入AI数字人会话详情页，数字人没有任何反馈。现象：1)发送消息后UI不展示发送内容，无AI回复；2)下拉刷新后UI展示发送内容，但AI回复仍没有。第二次启动后正常。

## 排查过程

1. 检查跳转逻辑 → 代码正常
2. 断点调试源码 → 检查loadData和hasFirstLoadData
3. 检查aiUserAccid → 发现第一次获取为nil
4. 检查初始化时机 → 发现初始化后太快调用login方法导致

**关键发现**：初始化之后太快调用login方法，导致AI用户信息未完全初始化，aiUserAccid为nil

## 问题原因

初始化之后太快调用login方法，导致AI用户信息未完全初始化，aiUserAccid为nil

## 解决方案

方案1：设置NEAIUserManager.shared.setProvider后，监听NEAIUserManager.shared.addAIUserChangeListener的onAIUserChanged回调，触发后再给数字人发消息。方案2：避免初始化后立即调用login，确保AI用户管理器初始化完成。

## 其他触发场景

