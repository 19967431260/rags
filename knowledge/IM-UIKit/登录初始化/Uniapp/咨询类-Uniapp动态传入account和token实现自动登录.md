---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-UIKit
feature: 登录初始化
platform: Uniapp
title: Uniapp动态传入account和token实现自动登录
root_cause: NIM SDK全局只能初始化一次，多个页面初始化会导致冲突
solution: 在App.vue中进行NIM初始化，通过动态传入account和token实现自动登录。不要在多个页面重复初始化，避免页面销毁导致连接断开。参考文档：https://doc.yunxin.163.com/messaging-uikit/guide/jgwMDI2NTU?platform=uniapp
customers: ['深圳利好副业科技有限公司']
source: chat_history
tags: ['IM-UIKit', 'Uniapp', '自动登录', 'initNim', 'V10', '动态登录']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：Uniapp动态传入account和token实现自动登录

## 问题详情

**现象**：
客户在Uniapp项目中使用IM V10 UIKit，需要实现动态传入account和token进行自动登录，而不是写死在App.vue中。客户尝试在登录页面获取到用户信息后调用app.initNim({ account: res.imAccid, token: res.imToken })，但发现删除App.vue中的account和token后页面报错，或在其他页面执行登录后切换回会话页面仍显示App.vue中设置的账号。

## 排查过程

1. 客户尝试在test.vue页面动态传入account和token执行登录
2. 发现删除App.vue中的写死账号后页面报错
3. 技术支持指出全局只能初始化一次，不要多个页面初始化
4. 建议最好放在App.vue中，放在其他页面会随页面销毁而销毁

## 问题原因

NIM SDK全局只能初始化一次，多个页面初始化会导致冲突

## 解决方案

在App.vue中进行NIM初始化，通过动态传入account和token实现自动登录。不要在多个页面重复初始化，避免页面销毁导致连接断开。参考文档：https://doc.yunxin.163.com/messaging-uikit/guide/jgwMDI2NTU?platform=uniapp

## 其他触发场景

（合并时在此处追加）
