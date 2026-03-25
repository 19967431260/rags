---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 音视频通话
platform: iOS
title: iOS发布时NERtcAiDenoise.framework包含bitcode导致验证失败
root_cause: NERtc SDK框架包含bitcode，而Apple已弃用bitcode，导致App Store验证失败。
solution: 使用命令去除框架中的bitcode。参考官方文档：https://doc.yunxin.163.com/nertc/faq/Tg1NjA4Mzk?platform=client ，执行strip-bitcode脚本处理相关framework后重新打包。
customers: ["明康惠"]
source: chat_history
tags: ["bitcode", "iOS发布", "NERtcAiDenoise", "Flutter", "Validation failed"]
created: 2025-05-27
updated: 2025-03-20
---

## 问题：iOS iOS发布时NERtcAiDenoise.framework包含bitcode导致验证失败

## 问题详情

**现象**：
Flutter项目使用nertc_core: ^5.5.101插件，iOS端发布到App Store时验证失败，错误信息：Invalid Executable. The executable 'Runner.app/Frameworks/NERtcAiDenoise.framework/NERtcAiDenoise' contains bitcode。

**环境信息**：
- SDK 版本：
- 系统版本 / 设备：
- 平台：iOS

## 排查过程



## 问题原因

NERtc SDK框架包含bitcode，而Apple已弃用bitcode，导致App Store验证失败。

## 解决方案

使用命令去除框架中的bitcode。参考官方文档：https://doc.yunxin.163.com/nertc/faq/Tg1NjA4Mzk?platform=client ，执行strip-bitcode脚本处理相关framework后重新打包。

## 其他触发场景

