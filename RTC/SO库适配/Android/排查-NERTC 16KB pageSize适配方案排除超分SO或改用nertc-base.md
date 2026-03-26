---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: SO库适配
platform: Android
title: NERTC 16KB pageSize适配方案排除超分SO或改用nertc-base
root_cause: 5.8.10版本中libNERtcSuperResolution.so（超分功能）未做16KB pageSize适配，客户未使用超分功能但仍打包了该SO
solution: 方案1（推荐）：将api 'com.netease.yunxin:nertc:5.8.10'改为api 'com.netease.yunxin:nertc-base:5.8.10'（nertc-base不包含超分库）；方案2：在build.gradle中packagingOptions { exclude 'lib/.../libNERtcSuperResolution.so' }排除超分SO
customers: ["南宁市懂卿科技有限公司"]
source: chat_history
tags: ["16KB pageSize","NERTC","Android 15","SO适配","nertc-base"]
created: 2025-08-25
updated: 2026-03-26
---

## 问题：Android NERTC 16KB pageSize适配方案排除超分SO或改用nertc-base

## 问题详情

**现象**：
客户反映部分SDK的SO库未适配Android 16KB pageSize，NERTC版本5.8.10。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：5.8.10
- 系统版本 / 设备：Android（16KB pageSize）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供SO库适配问题截图，NERTC 5.8.10 → 确认问题
2. 客服确认5.6.50及以上版本已支持16KB pageSize → 版本确认
3. 客服排查发现只有超分库libNERtcSuperResolution.so不符合规则 → 定位到具体SO
4. 客服建议排除该SO（超分功能客户未使用）→ 方案
5. 进一步建议将api nertc:5.8.10改为api nertc-base:5.8.10即可解决 → 推荐方案

**关键发现**：5.8.10版本中libNERtcSuperResolution.so（超分功能）未做16KB pageSize适配，客户未使用超分功能但仍打包了该SO

## 问题原因

5.8.10版本中libNERtcSuperResolution.so（超分功能）未做16KB pageSize适配，客户未使用超分功能但仍打包了该SO。

## 解决方案

方案1（推荐）：将api 'com.netease.yunxin:nertc:5.8.10'改为api 'com.netease.yunxin:nertc-base:5.8.10'（nertc-base不包含超分库）；方案2：在build.gradle中packagingOptions { exclude 'lib/.../libNERtcSuperResolution.so' }排除超分SO。

## 其他触发场景

（合并时在此处追加）
