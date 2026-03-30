---
track_type: 排查类
sub_type: 配置开通咨询
product: IM-SDK
feature: 推送
platform: Android
title: OPPO推送配置错误
root_cause: 云信后台配置的OPPO推送证书与OPPO后台的appkey不一致（填成了ID）。
solution: 1. 确保云信后台配置的推送证书与OPPO后台的appkey一致；2. 使用消息推送里的appkey，不是应用ID；3. 修改后证书更新需要几分钟到半小时去灰度，可重新创建一本。
customers: ["VIP云信-四川斯特雅科技有限责任公司"]
source: chat_history
tags: ["OPPO推送", "证书配置", "appkey", "Android"]
created: 2025-11-12
updated: 2026-03-20
---

## 问题：Android OPPO推送配置错误

## 问题详情

**现象**：
接入OPPO离线推送，能收到消息但离线推送没有。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认接收方处于app杀死状态且未登出；2. 检查控制台日志是否有token生成；3. 核对云信后台配置的推送证书和OPPO后台的appkey是否一致。

**关键发现**：

## 问题原因

云信后台配置的OPPO推送证书与OPPO后台的appkey不一致（填成了ID）。

## 解决方案

1. 确保云信后台配置的推送证书与OPPO后台的appkey一致；2. 使用消息推送里的appkey，不是应用ID；3. 修改后证书更新需要几分钟到半小时去灰度，可重新创建一本。

## 其他触发场景

