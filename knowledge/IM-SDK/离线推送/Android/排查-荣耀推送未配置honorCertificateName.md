---
track_type: "排查类"
sub_type: "集成类"
product: "IM-SDK"
feature: "离线推送"
platform: "Android"
title: "荣耀推送未配置honorCertificateName"
root_cause: "未配置荣耀推送的honorCertificateName，导致荣耀推送注册失败。"
solution: "需要配置honorCertificateName，参考云信荣耀推送集成文档进行配置。"
customers: ["FVIP云信-深圳富旅奇缘"]
source: "chat_history"
tags: ["荣耀", "honor", "离线推送", "honorCertificateName", "注册失败"]
created: "2025-09-10"
updated: "2026-03-20"
---

## 问题：Android 荣耀推送未配置honorCertificateName

## 问题详情

**现象**：
荣耀手机收不到离线推送。

## 排查过程

1. 检查日志发现honor推送没有注册成功
2. 没有看到honor的配置和初始化
3. 确认未配置honorCertificateName

## 问题原因

未配置荣耀推送的honorCertificateName，导致荣耀推送注册失败。

## 解决方案

需要配置honorCertificateName，参考云信荣耀推送集成文档进行配置。

## 其他触发场景
