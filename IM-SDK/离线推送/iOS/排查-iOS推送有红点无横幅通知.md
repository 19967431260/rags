---
track_type: "排查类"
sub_type: "集成类"
product: "IM-SDK"
feature: "离线推送"
platform: "iOS"
title: "iOS推送有红点无横幅通知"
root_cause: "iOS推送证书过期导致token无法生成"
solution: "更新iOS推送证书，参考文档：https://faq.yunxin.163.com/#KB0074"
customers: ["广州还行"]
source: "chat_history"
tags: ["iOS推送", "证书过期", "token", "横幅通知"]
created: "2025-09-12"
updated: "2026-03-20"
---

## 问题：iOS iOS推送有红点无横幅通知

## 问题详情

**现象**：
iPhone应用icon有红点提示但没有横幅通知，设备通知设置已打开。

## 排查过程

1. 客户提供accid、appkey和时间点
2. 技术人员查询发现设备推送token未生成
3. 客户自查发现iOS证书已过期

## 问题原因

iOS推送证书过期导致token无法生成

## 解决方案

更新iOS推送证书，参考文档：https://faq.yunxin.163.com/#KB0074

## 其他触发场景
