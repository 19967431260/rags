---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 登录逻辑
platform: Uniapp
title: Uniapp应用消息发送失败未走登录逻辑
root_cause: onLaunch生命周期内的store判断逻辑可能阻止了登录流程执行
solution: 1. 在关键节点添加日志上报以便排查问题\n2. 或移除该判断逻辑，确保登录流程正常执行\n3. 检查应用生命周期内登录逻辑的调用时机
customers: ['湖南梦话灵境网络科技有限公司']
source: chat_history
tags: ['消息发送失败', '登录逻辑', 'onLaunch', 'Uniapp', 'store']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：Uniapp Uniapp应用消息发送失败未走登录逻辑

## 问题详情

**现象**：
客户反馈消息发不出去，经排查发现应用没有发起登录请求。客户代码中在onLaunch生命周期内使用了store判断，可能导致登录逻辑被跳过。

## 排查过程

1. 客户反馈消息发不出去，提供截图显示错误\n2. 技术支持查看日志发现没有走登录逻辑\n3. 客户本地无法复现问题\n4. 检查客户代码发现onLaunch中有store判断逻辑\n5. 怀疑store未处理时走不到return逻辑，导致登录被跳过

## 问题原因

onLaunch生命周期内的store判断逻辑可能阻止了登录流程执行

## 解决方案

1. 在关键节点添加日志上报以便排查问题\n2. 或移除该判断逻辑，确保登录流程正常执行\n3. 检查应用生命周期内登录逻辑的调用时机

## 其他触发场景

（合并时在此处追加）
