---
track_type: 咨询类
sub_type: 功能实现咨询
product: IM-UIKit
feature: emoji表情
platform: HarmonyOS
title: UIKit V9与V10版本emoji表情无法互通
customers: []
source: chat_history
tags: []
created: 2025-02-01
updated: 2025-03-20
---

# UIKit V9与V10版本emoji表情无法互通

## 问题描述

客户使用V9版本安卓发送emoji，V10鸿蒙端接收后不显示emoji。V9版本使用的是早期开源kit，与当前UIKit的emoji表情规则不互通

## 解答

将V9的表情规则按照V10 UIKit的规则改造适配，参考云信提供的emoji规则JSON文件进行映射转换

## 标签

- emoji
- UIKit
- V9
- V10
- 鸿蒙
- Android
- 互通

## 客户

- 北京久幺幺

## 会话日期

2025-02-06
