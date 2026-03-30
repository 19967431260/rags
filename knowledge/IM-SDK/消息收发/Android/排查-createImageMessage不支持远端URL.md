---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: Android
title: createImageMessage不支持远端URL
root_cause: createImageMessage的imagePath参数只支持本地地址，不支持远端URL构建
solution: 非云信地址的图片只能通过自定义消息类型封装发送，接收方需要自行解析和渲染
customers: ["云信+乐次元"]
source: chat_history
tags: ["createImageMessage", "图片消息", "远端URL", "自定义消息"]
created: 2025-11-25
updated: 2026-03-20
---

## 问题：Android createImageMessage不支持远端URL

## 问题详情

**现象**：
使用createImageMessage发送图片时传入服务器图片地址（远端URL），报错文件不存在

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 用户反馈传入远端URL报文件不存在错误
2. 技术支持确认createImageMessage的imagePath只支持本地地址
3. 确认远端URL无法通过createImageMessage直接发送

**关键发现**：

## 问题原因

createImageMessage的imagePath参数只支持本地地址，不支持远端URL构建

## 解决方案

非云信地址的图片只能通过自定义消息类型封装发送，接收方需要自行解析和渲染

## 其他触发场景

