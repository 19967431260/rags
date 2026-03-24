---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息抄送
platform: 服务端
title: 消息抄送IPv6地址问题及解决方案
root_cause: link配置调整后，部分用户本地缓存导致使用IPv6
solution: 建议尽快支持IPv6解析，后续IPv6可能更普及；或等待缓存过期后自动恢复
customers: ['ISV云信-智慧丘比特-dx']
source: chat_history
tags: ['消息抄送', 'IPv6', 'link配置']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：服务端 消息抄送IPv6地址问题及解决方案

## 问题详情

**现象**：
客户反馈消息抄送出现IPv6格式地址，之前已通过关闭IPv6解决，但问题再次出现。

## 排查过程

1. 客户反馈部分账号抄送的是IPv6格式地址
2. 提供具体accid和时间点
3. 技术支持解释昨天调整了部分link配置，本地有缓存的用户可能使用IPv6
4. 建议客户尽快支持IPv6解析

## 问题原因

link配置调整后，部分用户本地缓存导致使用IPv6

## 解决方案

建议尽快支持IPv6解析，后续IPv6可能更普及；或等待缓存过期后自动恢复

## 其他触发场景

（合并时在此处追加）
