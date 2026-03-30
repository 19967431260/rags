---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 屏幕共享
platform: Uniapp/iOS
title: Uniapp iOS端屏幕共享对端看不到画面
root_cause: iOS屏幕共享需要额外配置屏幕共享扩展和App Group，demo未完整展示
solution: 参考官方文档配置iOS屏幕共享扩展和App Group，确保辅流画面正确渲染
customers: ['怀化市鹤城区星龙网络科技有限责任公司']
source: chat_history
tags: ['RTC', '音视频2.0', '屏幕共享', 'Uniapp', 'iOS']
created: 2025-01-06
updated: 2026-03-23
---

## 问题：Uniapp iOS端屏幕共享对端看不到画面

## 问题详情

**现象**：
客户使用Uniapp开发iOS端音视频，屏幕共享时对端看不到画面，但有声音，安卓端正常。

## 排查过程

1. 客户反馈iOS屏幕共享看不到画面，安卓端正常
2. 检查发现demo可能缺少辅流画面展示逻辑
3. 确认需要配置屏幕共享扩展和相关的App Group

## 问题原因

iOS屏幕共享需要额外配置屏幕共享扩展和App Group，demo未完整展示

## 解决方案

参考官方文档配置iOS屏幕共享扩展和App Group，确保辅流画面正确渲染

## 其他触发场景

（合并时在此处追加）
