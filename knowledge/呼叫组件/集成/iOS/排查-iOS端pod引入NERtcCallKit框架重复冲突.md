---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 集成
platform: iOS
title: iOS端pod引入NERtcCallKit框架重复冲突
root_cause: 直接引入NERtcCallKit会包含完整的NIMSDK_LITE，与项目中已有的IM SDK版本冲突，导致重复的framework。
solution: 使用pod子模块方式引入，避免框架冲突：\npod 'NERtcCallKit/NOS_Special', '3.5.0'\npod 'NERtcCallUIKit/NOS_Special', '3.5.0'\npod 'NERtcSDK/RtcBasic'\n\n如果NOS_Special仍有冲突，可尝试FCS_Special子模块。
customers: ["东莞市仁众丽科技有限公司"]
source: chat_history
tags: ["NERtcCallKit","YXArtemis","Multiple commands","pod","iOS"]
created: 2025-08-05
updated: 2026-03-26
---

## 问题：iOS iOS端pod引入NERtcCallKit框架重复冲突

## 问题详情

**现象**：
iOS项目引入NERtcCallKit时报错：Multiple commands produce '/Users/.../Frameworks/YXArtemis.framework'，有两个版本的NIMSDK_LITE冲突。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认项目情况 → Flutter项目调用原生音视频UI组件
2. 确认已有依赖 → 已有nim_chatkit_ui 10.1.0等IM相关pod
3. 确认NERtcCallKit版本 → 使用3.5.0
4. 解决方案：使用子模块方式引入，避免框架冲突

**关键发现**：直接引入NERtcCallKit会包含完整的NIMSDK_LITE，与项目中已有的IM SDK版本冲突，导致重复的framework。

## 问题原因

直接引入NERtcCallKit会包含完整的NIMSDK_LITE，与项目中已有的IM SDK版本冲突，导致重复的framework。

## 解决方案

使用pod子模块方式引入，避免框架冲突：
pod 'NERtcCallKit/NOS_Special', '3.5.0'
pod 'NERtcCallUIKit/NOS_Special', '3.5.0'
pod 'NERtcSDK/RtcBasic'

如果NOS_Special仍有冲突，可尝试FCS_Special子模块。

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
