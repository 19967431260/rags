---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 拍照上传
platform: Flutter
title: Flutter UIKit iOS拍照上传图片蓝光问题
root_cause: Flutter UIKit拍照组件本地存储图片处理有问题
solution: 使用自己的相机库替代UIKit默认拍照组件解决问题。
customers: ["南京芷间科技有限公司"]
source: chat_history
tags: ["Flutter", "UIKit", "拍照", "蓝光", "iOS"]
created: 2025-06-05
updated: 2025-03-23
---

## 问题：Flutter Flutter UIKit iOS拍照上传图片蓝光问题

## 问题详情

**现象**：
Flutter版本使用UIKit拍照上传出现蓝光问题，选择图片正常，iOS有问题，Android正常。

## 排查过程

1. 使用官方demo测试
2. 对比Flutter版本
3. 确认本地存储图片有问题
4. 客户使用自己的相机库解决问题

**关键发现**：Flutter UIKit拍照组件本地存储图片处理有问题

## 问题原因

Flutter UIKit拍照组件本地存储图片处理有问题

## 解决方案

使用自己的相机库替代UIKit默认拍照组件解决问题。

## 其他触发场景

