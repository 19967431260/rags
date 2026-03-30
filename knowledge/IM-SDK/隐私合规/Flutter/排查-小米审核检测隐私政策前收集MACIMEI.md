---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 隐私合规
platform: Flutter
title: 小米审核检测隐私政策前收集MAC/IMEI
root_cause: mobile_scanner扫码插件在初始化时创建OrientationEventListener，触发SensorManager获取传感器列表，被小米审核检测为隐私政策前收集信息
solution: 1. 延迟插件注册：在MainActivity中重写configureFlutterEngine，不自动注册插件，用户同意后手动调用registerPluginsAfterConsent
2. 或使用flutter pub deps检查依赖树，排查问题库
3. 考虑更换扫码方案为谷歌相机+二维码识别
customers: ["VIP云信-重庆橙心物流网络"]
source: chat_history
tags: ["小米审核", "隐私合规", "MAC", "IMEI", "传感器", "Flutter"]
created: 2025-11-03
updated: 2026-03-20
---

## 问题：Flutter 小米审核检测隐私政策前收集MAC/IMEI

## 问题详情

**现象**：
小米应用审核提示：APP以隐私政策弹窗形式向用户明示收集规则，未经用户同意，存在收集设备MAC地址、IMEI等信息的行为。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查SDK初始化位置 → 已移至隐私同意后
2. 检查原生层代码 → 发现推送SDK初始化在原生层
3. 延迟原生插件加载 → 问题依然存在
4. 分析堆栈 → 发现mobile_scanner插件在初始化时获取传感器
**关键发现**：mobile_scanner插件在注册时触发OrientationEventListener，导致获取传感器列表

**关键发现**：

## 问题原因

mobile_scanner扫码插件在初始化时创建OrientationEventListener，触发SensorManager获取传感器列表，被小米审核检测为隐私政策前收集信息

## 解决方案

1. 延迟插件注册：在MainActivity中重写configureFlutterEngine，不自动注册插件，用户同意后手动调用registerPluginsAfterConsent
2. 或使用flutter pub deps检查依赖树，排查问题库
3. 考虑更换扫码方案为谷歌相机+二维码识别

## 其他触发场景

