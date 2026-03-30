---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: ESP32硬件集成
platform: 通用
title: ESP32 S3板子config文件读取失败
root_cause: ""
solution: 切换到v1.2.2正式版分支，在idf.py menuconfig中配置相关参数，参考《ESP32板子跑通线上Demo》文档进行配置。
customers: ["米团数智"]
source: chat_history
tags: ["ESP32", "S3", "config", "v1.2.2", "demo"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：通用 ESP32 S3板子config文件读取失败

## 问题详情

**现象**：
使用ESP32 S3板子运行nertc-esp32-demo时，config文件无法正常读取。客户使用的是GitHub上v1.2.2-beta分支版本。

## 解决方案

切换到v1.2.2正式版分支，在idf.py menuconfig中配置相关参数，参考《ESP32板子跑通线上Demo》文档进行配置。

## 其他触发场景

