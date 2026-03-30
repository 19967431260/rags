---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 录制
platform: Uniapp
title: NERTC Uniapp远端视频组件高度固定
root_cause: 组件默认渲染模式导致高度不随父容器自适应
solution: 在 setupLocalVideoCanvas 和 setupRemoteVideoCanvas 调用时传入 renderMode: 1 参数。参考文档：https://doc.yunxin.163.com/nertc/guide/DEyODkyMzU?platform=uniapp
customers: ["成都神鸟互联网医院有限公司"]
source: chat_history
tags: ["renderMode","NERTCRemoteViewComponent","远端视频","高度固定","Uniapp"]
created: 2025-08-14
updated: 2026-03-26
---

## 问题：Uniapp NERTC Uniapp远端视频组件高度固定

## 问题详情

**现象**：
客户在使用 NERTCUniPluginSDK-NERTCRemoteViewComponent 远端视频组件时，组件高度固定无法跟随父元素自适应，上下有空白间隙。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服建议设置 renderMode 参数 → 解决方案

**关键发现**：组件默认渲染模式导致高度不随父容器自适应

## 问题原因

组件默认渲染模式导致高度不随父容器自适应

## 解决方案

在 setupLocalVideoCanvas 和 setupRemoteVideoCanvas 调用时传入 renderMode: 1 参数。参考文档：https://doc.yunxin.163.com/nertc/guide/DEyODkyMzU?platform=uniapp

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
