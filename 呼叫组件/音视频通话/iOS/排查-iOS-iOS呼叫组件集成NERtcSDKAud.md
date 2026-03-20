---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 音视频通话
platform: iOS
title: iOS呼叫组件集成NERtcSDKAudio编译报错
root_cause: NERtcSDKAudio版本尚未更新，与Xcode 16.4/Swift 6.1不兼容
solution: 暂时使用完整版NERtcSDK替代NERtcSDKAudio，等待NERtcSDKAudio更新后再切换
customers: ["xhsp"]
source: chat_history
tags: ["呼叫组件", "NERtcSDKAudio", "编译报错", "Swift 6.1", "Xcode 16.4"]
created: 2025-11-13
updated: 2026-03-20
---

## 问题：iOS iOS呼叫组件集成NERtcSDKAudio编译报错

## 问题详情

**现象**：
客户集成呼叫组件NERtcCallKit 3.8.0时，使用NERtcSDKAudio音频版SDK（为了减小包体积）在Xcode 16.4上编译报错，提示需要支持Swift 6.1版本。

**排查过程**：
1. 客户使用NERtcSDKAudio替换NERtcSDK以减小包体积
2. 新建Swift项目测试仍有同样问题
3. 换回NERtcSDK后正常

## 问题原因

NERtcSDKAudio版本尚未更新，与Xcode 16.4/Swift 6.1不兼容

## 解决方案

暂时使用完整版NERtcSDK替代NERtcSDKAudio，等待NERtcSDKAudio更新后再切换
