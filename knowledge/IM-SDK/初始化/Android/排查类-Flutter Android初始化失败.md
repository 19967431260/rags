---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 初始化
platform: Android
title: Flutter Android初始化失败
root_cause: AndroidManifest.xml中点击跳转启动页配置为云信demo的主页，应改为客户自己的首页
solution: 将AndroidManifest.xml中点击跳转的Activity改为客户自己的主页面Activity全类名，而非云信demo的MainActivity
customers: ['宁波未科网络科技有限公司']
source: chat_history
tags: ['Flutter', 'Android', '初始化失败', 'MainActivity', '启动页', 'iOS正常']
created: 2025-01-09
updated: 2026-03-23
---

## 问题：Flutter Android初始化失败

## 问题详情

**现象**：
Flutter项目Android运行初始化失败，iOS正常。

## 排查过程

1. 客户反馈Android初始化失败
2. 建议检查Android配置
3. 客户确认配置已添加
4. 要求提供logcat日志
5. 分析日志发现启动页配置问题
6. 发现客户配置了com.netease.yunxin.app.flutter.im.MainActivity
7. 告知需要改成客户自己的主页面Activity
8. 客户修改后初始化成功

## 问题原因

AndroidManifest.xml中点击跳转启动页配置为云信demo的主页，应改为客户自己的首页

## 解决方案

将AndroidManifest.xml中点击跳转的Activity改为客户自己的主页面Activity全类名，而非云信demo的MainActivity

## 其他触发场景

（合并时在此处追加）
