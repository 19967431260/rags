---
track_type: 排查类
sub_type: 集成类
product: 音视频SDK
feature: 视频截图
platform: iOS
title: iOS端摄像头被占用时takeRemoteSnapshot回调不触发
root_cause: takeRemoteSnapshot是异步接口，当摄像头被系统相机占用时，接口本身会失败（不返回0），但失败时不会触发回调。业务层需要先判断接口返回值再做后续处理。
solution: 调用takeRemoteSnapshot前先判断接口同步返回结果值是否正确（返回值==0），如果返回非0则不需要等待异步回调（回调不会触发）。示例代码：NIMChatManagerInputFileResult *result = [[NIMSDK sharedSDK].chatManager takeRemoteSnapshot:... session:... completion:...]; if (result.error.code != 0) { // 直接处理失败，不需要等待回调 }
customers: ["臻络"]
source: chat_history
tags: ["takeRemoteSnapshot","摄像头占用","回调","iOS","截图"]
created: 2025-08-04
updated: 2026-03-26
---

## 问题：iOS iOS端摄像头被占用时takeRemoteSnapshot回调不触发

## 问题详情

**现象**：
iOS端用户A使用系统相机期间，Android用户调用takeRemoteSnapshot对iOS用户截图，iOS端没有任何回调。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认回调不触发是因为需要先判断接口返回值是否正确 → 定位到判断逻辑缺失

**关键发现**：takeRemoteSnapshot是异步接口，当摄像头被系统相机占用时，接口本身会失败（不返回0），但失败时不会触发回调

## 问题原因

takeRemoteSnapshot是异步接口，当摄像头被系统相机占用时，接口本身会失败（不返回0），但失败时不会触发回调。业务层需要先判断接口返回值再做后续处理。

## 解决方案

调用takeRemoteSnapshot前先判断接口同步返回结果值是否正确（返回值==0），如果返回非0则不需要等待异步回调（回调不会触发）。
示例代码：
```objc
NIMChatManagerInputFileResult *result = [[NIMSDK sharedSDK].chatManager takeRemoteSnapshot:... session:... completion:...];
if (result.error.code != 0) {
    // 直接处理失败，不需要等待回调
}
```

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
