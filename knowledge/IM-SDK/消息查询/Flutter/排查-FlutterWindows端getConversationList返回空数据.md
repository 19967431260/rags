---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 消息查询
platform: Flutter
title: Flutter Windows端getConversationList返回空数据
root_cause: 1. release模式enableCloudConversation未开启，导致本地无缓存时无法从云端拉取会话列表；2. Flutter Windows需要使用NimPCSDK而非通用SDK
solution: 1. 在初始化时设置enableCloudConversation: true开启云端会话；2. Windows和Mac平台必须使用NimPCSDK，参考：https://doc.yunxin.163.com/messaging-uikit/guide/Dk0OTEzOTY?platform=flutter#第三步配置会话存储模式；3. 注意：Flutter uikit对Windows的支持存在已知限制，可能遇到其他兼容性问题
customers: ["voiceverse.org"]
source: chat_history
tags: ["getConversationList", "Flutter", "Windows", "enableCloudConversation", "NimPCSDK", "release"]
created: 2025-08-22
updated: 2025-08-22
---

## 问题：Flutter Flutter Windows端getConversationList返回空数据

## 问题详情

**现象**：
Flutter编译到Windows平台，debug模式会话列表正常显示，但打包成exe后会话列表为空。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：Flutter Windows
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服拉取SDK日志分析 → 获取排查信息
2. 检查初始化配置发现enableCloudConversation=false → 发现配置问题
3. 根因：release模式初始化时未开启云端会话 → 定位根因
4. 客户修改后仍无效，最终确认需要使用PC专用SDK → 进一步定位

**关键发现**：Flutter uikit Windows平台的会话列表功能依赖enableCloudConversation配置，且需要使用NimPCSDK

## 问题原因

1. release模式enableCloudConversation未开启，导致本地无缓存时无法从云端拉取会话列表
2. Flutter Windows需要使用NimPCSDK而非通用SDK

## 解决方案

1. 在初始化时设置enableCloudConversation: true开启云端会话
2. Windows和Mac平台必须使用NimPCSDK，参考：https://doc.yunxin.163.com/messaging-uikit/guide/Dk0OTEzOTY?platform=flutter#第三步配置会话存储模式
3. 注意：Flutter uikit对Windows的支持存在已知限制，可能遇到其他兼容性问题

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
