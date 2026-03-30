---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 悬浮窗
platform: Android
title: Android音视频通话退后台后悬浮窗消失
root_cause: CommonCallActivity发布源码中未实现退后台时的悬浮窗展示逻辑，而demo中包含此逻辑
solution: 在CommonCallActivity中重写onStop方法，调用doShowFloatingWindowInner()内部逻辑，根据callEngine.callInfo.callStatus判断权限后，使用CallUIFloatingWindowMgr.showFloat(this.applicationContext)+finish()显示悬浮窗
customers: ["一智科技（成都）有限公司"]
source: chat_history
tags: ["CallKit","悬浮窗","Android","Flutter","enableFloatingWindow","doShowFloatingWindowInner"]
created: 2025-08-14
updated: 2026-03-26
---

## 问题：Android Android音视频通话退后台后悬浮窗消失

## 问题详情

**现象**：
客户使用Flutter桥接原生CallKit，Android端音视频通话界面退出后台后重新打开主程序，悬浮窗消失。已开启enableFloatingWindow配置。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：Flutter桥接原生CallKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供视频和截图 → 获取复现材料
2. 客服确认使用Flutter桥接原生CallKit → 技术栈确认
3. 确认开启enableFloatingWindow后仍不生效 → 配置本身没问题
4. 客服分析原因：demo做了退后台处理但发布源码里没写 → 根因定位
5. 根因：CommonCallActivity中缺少onStop生命周期的小窗逻辑 → 根因确认
6. 方案：重写onStop调用doShowFloatingWindowInner()内部逻辑，判断权限后调用CallUIFloatingWindowMgr.showFloat()+finish() → 解决方案明确

**关键发现**：CommonCallActivity发布源码中未实现退后台时的悬浮窗展示逻辑，而demo中包含此逻辑

## 问题原因

CommonCallActivity发布源码中未实现退后台时的悬浮窗展示逻辑，而demo中包含此逻辑。

## 解决方案

在CommonCallActivity中重写onStop方法，调用doShowFloatingWindowInner()内部逻辑，根据callEngine.callInfo.callStatus判断权限后，使用CallUIFloatingWindowMgr.showFloat(this.applicationContext)+finish()显示悬浮窗。

## 其他触发场景

（合并时在此处追加）
