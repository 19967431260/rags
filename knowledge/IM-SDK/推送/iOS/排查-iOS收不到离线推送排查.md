---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 推送
platform: iOS
title: iOS收不到离线推送排查
root_cause: 
solution: 检查updateApnsToken是否正确上报token，确认证书apnsCername已正确传入。查看SDK日志确认具体原因
customers: ['VIP云信-广州氧气宝宝教育咨询服务有限公司']
source: chat_history
tags: ['推送', 'iOS', 'apnsToken', '离线推送', '证书']
created: 2025-01-02
updated: 2026-03-23
---

## 问题：iOS iOS收不到离线推送排查

## 问题详情

**现象**：
iOS端收不到离线推送，需要排查证书和token配置

## 排查过程

1. 检查apnsToken上报 → 确认是否有updateApnsToken
2. 检查证书配置 → 确认apnsCername是否正确传入

## 问题原因



## 解决方案

检查updateApnsToken是否正确上报token，确认证书apnsCername已正确传入。查看SDK日志确认具体原因

## 其他触发场景

（合并时在此处追加）
