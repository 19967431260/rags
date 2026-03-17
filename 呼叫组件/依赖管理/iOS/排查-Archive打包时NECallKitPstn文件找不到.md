---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 依赖管理
platform: iOS
title: Archive打包时NECallKitPstn文件找不到
root_cause: NECallKitPstn的podspec中NERtcCallKit依赖未改成NERtcCallKit/NOS_Special。
solution: 修改NECallKitPstn的podspec，将NERtcCallKit依赖改为NERtcCallKit/NOS_Special。NECallKitPstn是单独功能，呼叫组件和会议不会用到，但NECallKitPstn会用到NERtcCallKit。
customers: ["成都新势界"]
source: chat_history
tags: ["Archive","NECallKitPstn","NOS_Special","打包错误"]
created: 2026-02-03
updated: 2026-03-17
---

## 问题：iOS Archive打包时NECallKitPstn文件找不到

## 问题详情

**现象**：
使用NOS_Special版本后编译通过，但Archive打包时提示NECallKitPstn相关文件找不到。

## 问题原因

NECallKitPstn的podspec中NERtcCallKit依赖未改成NERtcCallKit/NOS_Special。

## 解决方案

修改NECallKitPstn的podspec，将NERtcCallKit依赖改为NERtcCallKit/NOS_Special。NECallKitPstn是单独功能，呼叫组件和会议不会用到，但NECallKitPstn会用到NERtcCallKit。

## 其他触发场景

