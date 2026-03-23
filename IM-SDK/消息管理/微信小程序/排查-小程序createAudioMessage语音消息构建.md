---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息管理
platform: 微信小程序
title: 小程序createAudioMessage语音消息构建
root_cause: ESM模式下上传模块与语音消息构建存在冲突
solution: ESM模式下需要注册必要模块，但上传模块可能与语音消息构建冲突。使用getRecorderManager录制的临时文件可以直接使用，能正常接收播放即可。
customers: ["一泓福瑞文化产业有限公司"]
source: chat_history
tags: ["createAudioMessage","语音消息","小程序","ESM"]
created: 2025-06-06
updated: 2025-06-06
---

## 问题：微信小程序 createAudioMessage语音消息构建

## 问题详情

**现象**：
客户咨询小程序createAudioMessage的audioPath参数限制，以及使用getRecorderManager录音后的临时文件是否可用。

**环境信息**：
- 平台：微信小程序
- 涉及API：createAudioMessage, getRecorderManager

## 排查过程

1. 确认ESM模式下需要注册上传模块 → 检查模块注册
2. 发现上传模块冲突导致构建失败 → 定位冲突点
3. 注释上传模块后恢复正常 → 验证解决方案

**关键发现**：ESM模式下上传模块与语音消息构建存在冲突

## 问题原因

ESM模式下上传模块与语音消息构建存在冲突

## 解决方案

ESM模式下需要注册必要模块，但上传模块可能与语音消息构建冲突。使用getRecorderManager录制的临时文件可以直接使用，能正常接收播放即可。

## 其他触发场景

