---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: ESP32集成
platform: 通用
title: ESP32 Demo需要16MB Flash才能运行
root_cause: Demo默认分区配置为16MB，8MB空间不足，需要单独适配。
solution: Demo必须使用16MB Flash的板子。8MB板子需要单独适配分区大小，目前没有适配计划。如需使用8MB板子，可基于demo自行适配分区配置。
customers: ["晨芯成科技"]
source: chat_history
tags: ["ESP32","16MB","8MB","分区表","Flash"]
created: 2026-02-05
updated: 2026-03-17
---

## 问题：通用 ESP32 Demo需要16MB Flash才能运行

## 问题详情

**现象**：
客户使用8MB Flash的ESP32开发板，选择8MB配置时报分区表地址重叠错误，v1和v2版本都无法运行。

## 问题原因

Demo默认分区配置为16MB，8MB空间不足，需要单独适配。

## 解决方案

Demo必须使用16MB Flash的板子。8MB板子需要单独适配分区大小，目前没有适配计划。如需使用8MB板子，可基于demo自行适配分区配置。

## 其他触发场景

