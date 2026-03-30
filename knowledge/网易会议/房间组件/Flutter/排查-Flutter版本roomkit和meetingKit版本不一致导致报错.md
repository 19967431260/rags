---
track_type: 排查类
sub_type: 集成类
product: 网易会议
feature: 房间组件
platform: Flutter
title: Flutter版本roomkit和meetingKit版本不一致导致报错
root_cause: roomkit和meetingKit版本不一致导致依赖冲突。
solution: 将roomkit和roomkit_interface版本统一为1.32.1，与meetingKit版本保持一致。
customers: ["安徽鼎校教育科技有限公司"]
source: chat_history
tags: ["Flutter", "roomkit", "meetingKit", "版本冲突", "依赖"]
created: 2025-02-13
updated: 2025-03-20
---

## 问题：Flutter Flutter版本roomkit和meetingKit版本不一致导致报错

## 问题详情

**现象**：
Mac端Flutter工程运行报错，检查发现.lock文件中meetingKit版本1.32.1，roomkit版本1.32.0，版本不一致。

**环境信息**：
- 平台：Flutter
- 设备：Mac
- meetingKit版本：1.32.1
- roomkit版本：1.32.0

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 检查.lock文件版本 → meetingKit 1.32.1，roomkit 1.32.0
2. 检查pubspec.yaml依赖配置
3. 统一版本号 → 将roomkit和roomkit_interface都改为1.32.1

**关键发现**：版本不一致导致依赖冲突

## 问题原因

roomkit和meetingKit版本不一致导致依赖冲突。

## 解决方案

将roomkit和roomkit_interface版本统一为1.32.1，与meetingKit版本保持一致。

## 其他触发场景
