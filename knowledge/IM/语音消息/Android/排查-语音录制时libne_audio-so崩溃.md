---
track_type: 排查类
sub_type: BUG问题
product: IM
feature: 语音消息
platform: Android
title: 语音录制时libne_audio.so崩溃
root_cause: SDK内部AudioRecord封装了降噪处理功能，在降噪算法（MMSE）计算过程中，boost库的数学函数出现溢出异常导致崩溃。
solution: **临时方案**：将云信AudioRecord录制接口换成系统原生语音录制API
**长期方案**：SDK后续版本会去掉降噪处理步骤，API保持不变，届时通知客户升级
customers: ["北京百骏天成科技"]
source: chat_history
tags: ["语音录制", "崩溃", "libne_audio.so", "降噪", "overflow_error", "Android"]
created: 2026-01-14
updated: 2026-03-15
---

## 问题：Android 语音录制时libne_audio.so崩溃

## 问题详情

**现象**：
客户反馈Android端语音录制时偶发崩溃，堆栈显示在libne_audio.so的降噪处理过程中出现overflow_error异常。崩溃位置：SpectrumRestorer_MMSE::apply -> boost::math相关函数。

## 排查过程

1. 分析堆栈 → 崩溃发生在降噪处理模块
2. 确认是否使用UIKit → 客户未使用
3. 定位问题 → SDK内部AudioRecord封装的降噪处理导致

## 问题原因

SDK内部AudioRecord封装了降噪处理功能，在降噪算法（MMSE）计算过程中，boost库的数学函数出现溢出异常导致崩溃。

## 解决方案

**临时方案**：将云信AudioRecord录制接口换成系统原生语音录制API
**长期方案**：SDK后续版本会去掉降噪处理步骤，API保持不变，届时通知客户升级
