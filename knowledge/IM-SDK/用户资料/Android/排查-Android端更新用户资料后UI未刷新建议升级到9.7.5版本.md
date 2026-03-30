---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 用户资料
platform: Android
title: Android端更新用户资料后UI未刷新建议升级到9.7.5版本
root_cause: Android端UIKit 9.6.4版本存在已知问题：更新用户资料后群聊会话页面UI未自动刷新；新版本9.7.5已修复
solution: Android端更新用户资料UI未刷新问题：升级UIKit到9.7.5版本；如仍有问题需提供可复现demo给云信排查
customers: ["西安麦游网络科技有限公司"]
source: chat_history
tags: ["Android","UIKit","用户资料","updateUserInfo","UI刷新","9.7.5"]
created: 2025-08-16
updated: 2026-03-26
---

## 问题：Android Android端更新用户资料后UI未刷新建议升级到9.7.5版本

## 问题详情

**现象**：
客户在设置页面更新本人用户资料后，返回群聊会话页面时UI未自动刷新。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：UIKit 9.6.4
- 系统版本 / 设备：Android
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供场景 → 确认问题
2. 客服确认最新版uikit应自动刷新 → 确认应该是自动的
3. 客户使用9.6.4版本 → 定位到版本问题
4. 建议升级到9.7.5版本试一下 → 确认解决方案

**关键发现**：Android端UIKit 9.6.4版本存在已知问题：更新用户资料后群聊会话页面UI未自动刷新

## 问题原因

Android端UIKit 9.6.4版本存在已知问题：更新用户资料后群聊会话页面UI未自动刷新；新版本9.7.5已修复

## 解决方案

Android端更新用户资料UI未刷新问题：升级UIKit到9.7.5版本；如仍有问题需提供可复现demo给云信排查

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
