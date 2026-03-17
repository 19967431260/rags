---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 集成
platform: iOS
title: iOS项目pod install时类定义处报错
root_cause: ""
solution: 在新项目中逐步引入旧项目代码,找到最简单的复现demo进行排查。导入方式可使用#import <NIMSDK/NIMSDK.h>或@import NIMSDK
customers: ["泰州迪赛网络科技有限公司"]
source: chat_history
tags: ["pod install", "iOS", "集成问题", "类定义报错", "NIMSDK"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：iOS iOS项目pod install时类定义处报错

## 问题详情

**现象**：
新建项目集成IM SDK没问题,但将旧项目的类导入后,pod install时在类定义处报错。

**环境信息**：
- 平台：iOS
- 已删除旧版本SDK

## 排查过程

1. 检查Podfile配置 → 配置正常
2. 删除Podfile.lock、Pods文件夹和xcworkspace重新pod install → 仍报错
3. 新建空项目测试 → 没问题
4. 将旧项目类导入新项目 → 复现报错
5. 确认删除旧版本SDK → 已删除

**关键发现**：问题出现在旧项目代码导入时,需要逐步引入找到最小复现场景

## 问题原因

根因未明确,需要进一步排查旧项目代码中的具体问题。

## 解决方案

在新项目中逐步引入旧项目代码,找到最简单的复现demo进行排查。导入方式可使用#import <NIMSDK/NIMSDK.h>或@import NIMSDK

## 其他触发场景

