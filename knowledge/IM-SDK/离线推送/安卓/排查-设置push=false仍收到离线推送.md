---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "离线推送"
platform: "安卓"
title: "设置push=false仍收到离线推送"
root_cause: "第三方回调中需使用pushEnable字段控制离线推送，且需放在modifyResponse层级下"
solution: "在第三方回调的modifyResponse中直接使用pushEnable字段（值为true/false），与body同层级"
customers: ["广州浪花"]
source: "chat_history"
tags: ["离线推送", "push", "pushEnable", "第三方回调", "modifyResponse"]
created: "2025-09-22"
updated: "2026-03-20"
---

## 问题：安卓 设置push=false仍收到离线推送

## 问题详情

**现象**：
客户设置push=false希望只在线推送不离线推送，但客户端仍收到离线推送。

## 排查过程

1. 客户提供消息ID
2. 技术人员核查发现回调中设置的是push字段而非pushEnable
3. 确认pushEnable需要放在modifyResponse下而非option层级

## 问题原因

第三方回调中需使用pushEnable字段控制离线推送，且需放在modifyResponse层级下

## 解决方案

在第三方回调的modifyResponse中直接使用pushEnable字段（值为true/false），与body同层级

## 其他触发场景
