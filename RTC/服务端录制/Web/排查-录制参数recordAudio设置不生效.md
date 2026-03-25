---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 服务端录制
platform: Web
title: 录制参数recordAudio设置不生效
root_cause: 客户端recordType参数未设置为1导致录制参数未生效
solution: 设置录制参数时需同时设置recordType=1，确保recordAudio和recordVideo参数能够正确传递到服务端。
customers: ["长沙银行"]
source: chat_history
tags: ["录制", "recordAudio", "recordVideo", "recordType", "WebRTC", "7.5"]
created: 2025-05-27
updated: 2025-03-20
---

## 问题：Web 录制参数recordAudio设置不生效

## 问题详情

**现象**：
音视频2.0 Web端设置recordAudio=1、recordVideo=0时，混合录制文件没有客户声音；设置recordAudio=1、recordVideo=1时才有声音。使用NIM_CrossPlatform_SDK_v7.5版本。

## 排查过程

**关键发现**：客户端recordType参数未设置为1导致录制参数未生效

## 问题原因

客户端recordType参数未设置为1导致录制参数未生效

## 解决方案

设置录制参数时需同时设置recordType=1，确保recordAudio和recordVideo参数能够正确传递到服务端。
