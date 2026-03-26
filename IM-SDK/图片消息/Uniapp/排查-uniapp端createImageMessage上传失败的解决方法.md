---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 图片消息
platform: Uniapp
title: uniapp端createImageMessage上传失败的解决方法
root_cause: uniapp中uni.chooseImage返回的tempFiles是File对象，而createImageMessage需要的是文件路径字符串
solution: 使用uni.chooseImage返回的tempFilePaths（文件路径字符串）而非tempFiles（File对象）作为createImageMessage的参数，即：nim.V2NIMMessageCreator.createImageMessage(tempFilePath)
customers: ["上海文攸网络科技有限公司","芜湖市乖巧虎科技有限公司"]
source: chat_history
tags: ["createImageMessage","Uniapp","图片消息","上传失败"]
created: 2025-08-03
updated: 2026-03-26
---

## 问题：Uniapp uniapp端createImageMessage上传失败的解决方法

## 问题详情

**现象**：
uniapp SDK调用createImageMessage接口，使用uni.chooseImage返回的tempFiles[0]（File对象）上传图片时报上传失败。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（无详细排查步骤，从会话提取）

**关键发现**：uniapp中uni.chooseImage返回的tempFiles是File对象，而createImageMessage需要的是文件路径字符串

## 问题原因

uniapp中uni.chooseImage返回的tempFiles是File对象，而createImageMessage需要的是文件路径字符串。

## 解决方案

使用uni.chooseImage返回的tempFilePaths（文件路径字符串）而非tempFiles（File对象）作为createImageMessage的参数，即：nim.V2NIMMessageCreator.createImageMessage(tempFilePath)。

## 其他触发场景

（合并时在此处追加）
