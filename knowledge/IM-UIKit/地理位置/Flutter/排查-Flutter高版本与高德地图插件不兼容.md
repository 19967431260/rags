---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 地理位置
platform: Flutter
title: Flutter高版本与高德地图插件不兼容
root_cause: Flutter版本过高（3.32.5），高德地图插件版本过低不兼容。地理位置插件已不再维护，高德也不再提供对应支持。
solution: 降级Flutter到3.19.6及以下版本，或使用百度地图等第三方开源地图方案替代。locationkit仅提供开源参考实现。
customers: ["东莞市仁众丽科技有限公司"]
source: chat_history
tags: ["Flutter", "高德地图", "版本兼容", "FlutterMain", "UIKit"]
created: 2026-02-04
updated: 2026-03-17
---

## 问题：Flutter Flutter高版本与高德地图插件不兼容

## 问题详情

**现象**：
Flutter 3.32.5版本集成UIKit的地理位置组件时，高德地图插件x_amap_flutter_map-1.0.2编译报错：找不到FlutterMain类和PluginRegistry.Registrar类。

## 问题原因

Flutter版本过高（3.32.5），高德地图插件版本过低不兼容。地理位置插件已不再维护，高德也不再提供对应支持。

## 解决方案

降级Flutter到3.19.6及以下版本，或使用百度地图等第三方开源地图方案替代。locationkit仅提供开源参考实现。

## 其他触发场景

（暂无）
