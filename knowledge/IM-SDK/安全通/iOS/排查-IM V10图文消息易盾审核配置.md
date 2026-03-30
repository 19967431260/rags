---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 安全通
platform: iOS
title: IM V10图文消息易盾审核配置
root_cause: antiSpamOption.content中的type字段与业务自定义的type冲突，导致易盾将图片url当作文本检测
solution: 确保antiSpamOption.content中的type与易盾定义一致：1表示文本，2表示图片。不要与业务自定义type混淆
customers: ['VIP云信-高途预见塔塔项目']
source: chat_history
tags: ['V10', '图文消息', '易盾', 'antiSpamOption', 'type']
created: 2025-01-20
updated: 2026-03-23
---

## 问题：iOS IM V10图文消息易盾审核配置

## 问题详情

**现象**：
iOS V10发送图文消息触发易盾审核，但返回广告嫌疑。content中的图片url被误判

## 排查过程

1. 分析antiSpamOption配置 → content传了图片url
2. 检查type参数 → type=1表示文本，但实际传的是图片url
3. 确认type定义冲突 → 业务type与易盾type不对应

## 问题原因

antiSpamOption.content中的type字段与业务自定义的type冲突，导致易盾将图片url当作文本检测

## 解决方案

确保antiSpamOption.content中的type与易盾定义一致：1表示文本，2表示图片。不要与业务自定义type混淆

## 其他触发场景

（合并时在此处追加）
