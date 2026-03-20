---
track_type: 排查类
sub_type: 集成类
product: IM-UIKit
feature: 依赖管理
platform: iOS
title: iOS UIKit SDWebImage版本冲突
root_cause: NETranscodingKit默认依赖的NERtcCallUIKit/NOS版本锁定SDWebImage 5.21.0，与NECommonUIKit依赖的5.21.3冲突。
solution: 使用special版本解决依赖冲突：
1. 将pod 'NETranscodingKit'改为pod 'NETranscodingKit/NOS_Special'
2. 删除Podfile.lock后重新pod install
3. 不要自行再依赖SDWebImage，使用SDK关联依赖的版本
customers: ["深圳市天启航空科技有限公司"]
source: chat_history
tags: ["SDWebImage", "依赖冲突", "CocoaPods", "NETranscodingKit", "iOS"]
created: 2025-11-12
updated: 2026-03-20
---

## 问题：iOS iOS UIKit SDWebImage版本冲突

## 问题详情

**现象**：
客户在使用iOS UIKit时，NECommonUIKit依赖SDWebImage 5.21.3，而NETranscodingKit依赖的NERtcCallUIKit/NOS锁定SDWebImage 5.21.0，导致CocoaPods版本冲突。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 分析依赖冲突 → NECommonUIKit需要SDWebImage 5.21.3，NETranscodingKit需要5.21.0
2. 尝试pod repo update → 无法解决
3. 检查Podfile.lock → 存在版本锁定
4. 使用special版本 → 使用NETranscodingKit/NOS_Special解决
**关键发现**：NETranscodingKit默认依赖与UIKit其他组件的SDWebImage版本不一致

**关键发现**：

## 问题原因

NETranscodingKit默认依赖的NERtcCallUIKit/NOS版本锁定SDWebImage 5.21.0，与NECommonUIKit依赖的5.21.3冲突。

## 解决方案

使用special版本解决依赖冲突：
1. 将pod 'NETranscodingKit'改为pod 'NETranscodingKit/NOS_Special'
2. 删除Podfile.lock后重新pod install
3. 不要自行再依赖SDWebImage，使用SDK关联依赖的版本

## 其他触发场景

