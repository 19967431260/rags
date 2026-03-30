---
track_type: 排查类
sub_type: 集成类
product: 呼叫组件
feature: 音视频通话
platform: iOS
title: iOS 18点视频通话闪退maskView异常
root_cause: iOS 18系统与呼叫组件2.5.0版本存在兼容性问题，maskView设置导致崩溃
solution: 升级呼叫组件至2.5.2版本，使用适配iOS 18的NERtcCallUIKit源码，参考：https://github.com/netease-kit/NEVideoCall-1to1/tree/callkit_v2.5.0/NLiteAVDemo-iOS-ObjC/CallKit/NERtcCallUIKit
customers: ["VIP云信-广州品爱科技"]
source: chat_history
tags: ["呼叫组件", "iOS 18", "闪退", "maskView", "兼容性问题"]
created: 2025-02-17
updated: 2026-03-20
---

## 问题：iOS iOS 18点视频通话闪退maskView异常

## 问题详情

**现象**：
iOS端呼叫组件在iOS 18.2.1系统上点击视频通话时报错闪退，错误信息为NSInternalInconsistencyException，提示maskView设置问题。iOS 16系统正常运行。

## 排查过程

1. 确认SDK版本为2.5.0
2. 测试官方demo在相同机型正常
3. 客户使用源码引入方式
4. 升级至2.5.2版本，调整NECoreKit和NECommonKit版本至9.7.0
5. 使用适配后的NERtcCallUIKit源码解决问题

## 问题原因

iOS 18系统与呼叫组件2.5.0版本存在兼容性问题，maskView设置导致崩溃

## 解决方案

升级呼叫组件至2.5.2版本，使用适配iOS 18的NERtcCallUIKit源码，参考：https://github.com/netease-kit/NEVideoCall-1to1/tree/callkit_v2.5.0/NLiteAVDemo-iOS-ObjC/CallKit/NERtcCallUIKit

## 其他触发场景
- [iOS] iOS 18点视频通话闪退maskView异常，来源：['VIP云信-广州品爱科技']，2026-03-20
- [iOS] iOS 18点视频通话闪退maskView异常，来源：['VIP云信-广州品爱科技']，2026-03-20

