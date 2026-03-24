---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 语音消息
platform: Uniapp
title: Uniapp发送语音消息文件上传失败
root_cause: 手动转换临时路径为file对象导致上传失败
solution: 直接使用uni.getRecorderManager()返回的临时路径调用createAudioMessage构建消息，SDK会自动处理上传
customers: ["黄骅市达祥知识产权服务有限公司"]
source: chat_history
tags: ["IM-SDK", "Uniapp", "语音消息", "文件上传"]
created: 2025-02-14
updated: 2026-03-20
---

## 问题：Uniapp Uniapp发送语音消息文件上传失败

## 问题详情

**现象**：
使用uni.getRecorderManager()录制语音后，通过临时路径获取file对象发送语音消息，上传失败。

## 排查过程

1. 客户使用uni.getRecorderManager()获取录音临时路径
2. 转换为file对象后发送语音消息
3. 文件上传失败
4. 正确做法是直接使用临时路径构建音频消息，无需手动转换file对象

## 问题原因

手动转换临时路径为file对象导致上传失败

## 解决方案

直接使用uni.getRecorderManager()返回的临时路径调用createAudioMessage构建消息，SDK会自动处理上传

## 其他触发场景
- [Uniapp] Uniapp发送语音消息文件上传失败，来源：['黄骅市达祥知识产权服务有限公司']，2026-03-20
- [Uniapp] Uniapp发送语音消息文件上传失败，来源：['黄骅市达祥知识产权服务有限公司']，2026-03-20

