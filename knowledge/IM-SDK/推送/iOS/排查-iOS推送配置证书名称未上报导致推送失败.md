---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: iOS
title: iOS推送配置证书名称未上报导致推送失败
root_cause: 上报推送token时配置的证书名称为占位符，未配置为控制台实际的证书名称
solution: 将上报推送token的证书名称改为控制台配置的一致名称（支持汉字）
customers: ['临沂久讯网络科技有限公司']
source: chat_history
tags: ['iOS', '推送', '证书', 'APNs', 'token上报']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：iOS iOS推送配置证书名称未上报导致推送失败

## 问题详情

**现象**：
iOS配置推送证书后，发送推送消息App无反应，进程已杀掉。

## 排查过程

1. 检查推送token上报情况
2. 发现代码中上报推送token时证书名称配置为<#请输入推送证书#>
3. 确认需要配置控制台一致的证书名称
**关键发现**：上报推送token时未配置正确的证书名称

## 问题原因

上报推送token时配置的证书名称为占位符，未配置为控制台实际的证书名称

## 解决方案

将上报推送token的证书名称改为控制台配置的一致名称（支持汉字）

## 其他触发场景

（合并时在此处追加）
