---
track_type: 排查类
sub_type: 使用问题
product: 呼叫组件
feature: 美颜集成
platform: Android
title: Android呼叫组件集成相芯美颜后对方黑屏
root_cause: 相芯美颜SDK的GL渲染未正确渲染
solution: 建议将setVideoCallback放到呼叫组件初始化后直接添加，不要在接通后才调用。美颜处理逻辑需要相芯确认GL渲染配置。
customers: ['VIP 云信-安徽航峰信息科技有限公司']
source: chat_history
tags: ['相芯美颜', '黑屏', '纹理渲染', 'setVideoCallback', 'Android']
created: 2025-01-08
updated: 2026-03-23
---

## 问题：Android Android呼叫组件集成相芯美颜后对方黑屏

## 问题详情

**现象**：
客户在使用NERtcCallUIKit组件集成相芯美颜时，使用纹理渲染方案（方案一），在setVideoCallback回调中处理美颜后，对方显示黑屏。客户代码中设置了视频配置为TEXTURE格式，并在回调中使用相芯FURenderer处理纹理。

## 排查过程

1. 确认注释掉美颜代码后正常 → 排除基础通话问题
2. 检查代码逻辑和初始化位置 → 客户是在接通后调用
3. 建议将setVideoCallback放到初始化后直接添加，而不是接通后
4. 最终确认是相芯侧GL渲染问题

## 问题原因

相芯美颜SDK的GL渲染未正确渲染

## 解决方案

建议将setVideoCallback放到呼叫组件初始化后直接添加，不要在接通后才调用。美颜处理逻辑需要相芯确认GL渲染配置。

## 其他触发场景

（合并时在此处追加）
