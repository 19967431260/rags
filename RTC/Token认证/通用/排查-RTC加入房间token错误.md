---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: Token认证
platform: 通用
title: RTC加入房间token错误
root_cause: token计算有误或已过期
solution: 检查token生成逻辑，确保token在有效期内，核对AppKey、accid、token三者匹配
customers: ['法正智能科技有限公司']
source: chat_history
tags: ['token', '加入房间', '认证', '过期', 'RTC']
created: 2025-01-07
updated: 2026-03-23
---

## 问题：通用 RTC加入房间token错误

## 问题详情

**现象**：
加入RTC房间失败，提示token错误，元旦前正常。

## 排查过程

1. 检查token生成逻辑
2. 确认token是否过期
3. 核对AppKey、accid、token匹配性

## 问题原因

token计算有误或已过期

## 解决方案

检查token生成逻辑，确保token在有效期内，核对AppKey、accid、token三者匹配

## 其他触发场景

（合并时在此处追加）
