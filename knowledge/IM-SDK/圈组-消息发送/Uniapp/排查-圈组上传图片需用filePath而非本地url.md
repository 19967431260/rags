---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 圈组-消息发送
platform: Uniapp
title: 圈组上传图片需用filePath而非本地url
root_cause: SDK内部上传依赖uni.uploadFile需要filePath参数而非本地url；APP端虚拟路径导致SDK拿不到正确的文件名参数
solution: Uniapp圈组上传图片：1.使用SDK的uploadFile方法并传入filePath参数而非本地url；2.若仍有问题可将文件信息放在消息的ext扩展字段里走自定义消息方式传图片url；3.APP端上传图片会丢失文件名，这是SDK限制只能业务侧自行处理
customers: ["家有学霸"]
source: chat_history
tags: ["圈组","Uniapp","图片上传","filePath","NOS"]
created: 2025-08-16
updated: 2026-03-26
---

## 问题：Uniapp 圈组上传图片需用filePath而非本地url

## 问题详情

**现象**：
Uniapp端圈组上传图片报错illegal file url，SDK要求使用filePath而非uniapp chooseImage返回的本地url。APP端使用url上传虽能成功但会丢失文件名，使用文件对象上传则报url错误。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：Uniapp + 圈组

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户上传图片报illegal file url错误 → 确认问题
2. 客服确认uniapp上传必须用filePath（SDK内部调用uni.uploadFile要求filePath）→ 根因确认
3. 客户反映chooseImage只有一种path → 确认
4. 客服与研发确认后给出临时方案：用filePath参数但需确保路径正确；也可将文件信息放在消息ext扩展字段里走自定义消息方式 → 方案
5. 最终方案：APP端上传图片建议直接用SDK的上传方法传filePath → 最终方案

**关键发现**：SDK内部上传依赖uni.uploadFile需要filePath参数而非本地url；APP端虚拟路径导致SDK拿不到正确的文件名参数

## 问题原因

SDK内部上传依赖uni.uploadFile需要filePath参数而非本地url；APP端虚拟路径导致SDK拿不到正确的文件名参数。

## 解决方案

Uniapp圈组上传图片：1.使用SDK的uploadFile方法并传入filePath参数而非本地url；2.若仍有问题可将文件信息放在消息的ext扩展字段里走自定义消息方式传图片url；3.APP端上传图片会丢失文件名，这是SDK限制只能业务侧自行处理。

## 其他触发场景

（合并时在此处追加）
