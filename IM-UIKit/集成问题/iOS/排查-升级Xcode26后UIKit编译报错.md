---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 集成问题
platform: iOS
title: 升级Xcode26后UIKit编译报错
root_cause: 版本号没有指定导致的报错
solution: 参照demo的Podfile指定版本号，将旧版的podfile.lock复制过去，重新pod解决NIM和iqkeyboard类型冲突
customers: ["时间在线"]
source: chat_history
tags: ["Xcode26","UIKit","编译错误","版本指定","podfile"]
created: 2026-02-02
updated: 2026-03-17
---

## 问题：iOS 升级Xcode26后UIKit编译报错

## 问题详情

**现象**：
升级Xcode26后，IM UIKit 9.5.0版本编译出现错误。UIKit是拉到本地进行修改的。

**环境信息**：
- SDK 版本：IM UIKit 9.5.0
- Xcode 版本：Xcode 26

## 排查过程

检查项未在会话中详细记录，直接定位到版本配置问题。

**关键发现**：版本号没有指定导致的报错

## 问题原因

版本号没有指定导致的报错

## 解决方案

1. 参照demo的Podfile指定版本号：https://github.com/netease-kit/nim-uikit-ios/blob/v9.5.0/Podfile
2. 按理说只要指定版本不会有这个问题
3. 客户通过将旧版的podfile.lock复制过去，重新pod解决了NIM和iqkeyboard类型冲突

## 其他触发场景

（暂无）
