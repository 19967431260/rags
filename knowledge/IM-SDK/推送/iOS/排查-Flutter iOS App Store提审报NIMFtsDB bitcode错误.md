---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: iOS
title: Flutter iOS App Store提审报NIMFtsDB bitcode错误
root_cause: Flutter iOS SDK集成的NIMFtsDB.framework包含了bitcode，而苹果已不支持bitcode。
solution: 在Podfile的post_install脚本中添加bitcode strip命令：\npost_install do |installer|\n  installer.pods_project.targets.each do |target|\n    if target.name == 'YXAlog'\n      `xcrun -sdk iphoneos bitcode_strip -r Pods/YXAlog/YXAlog_iOS.framework/YXAlog_iOS -o Pods/YXAlog/YXAlog_iOS.framework/YXAlog_iOS`\n    end\n  end\nend
customers: ["杭州云汽配配科技有限公司"]
source: chat_history
tags: ["bitcode","iOS","App Store","NIMFtsDB","Flutter","提审"]
created: 2025-08-21
updated: 2026-03-26
---

## 问题：iOS Flutter iOS App Store提审报NIMFtsDB bitcode错误

## 问题详情

**现象**：
客户Flutter iOS打包后提交App Store时报错：ITMS-90482: Invalid Executable - The executable 'Runner.app/Frameworks/NIMFtsDB.framework/NIMFtsDB' contains bitcode.

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客服确认 Flutter iOS SDK 的 NIMFtsDB.framework 包含 bitcode → 根因确认

**关键发现**：Flutter iOS SDK集成的NIMFtsDB.framework包含了bitcode，而苹果已不支持bitcode。

## 问题原因

Flutter iOS SDK集成的NIMFtsDB.framework包含了bitcode，而苹果已不支持bitcode。

## 解决方案

在Podfile的post_install脚本中添加bitcode strip命令：
post_install do |installer|
  installer.pods_project.targets.each do |target|
    if target.name == 'YXAlog'
      `xcrun -sdk iphoneos bitcode_strip -r Pods/YXAlog/YXAlog_iOS.framework/YXAlog_iOS -o Pods/YXAlog/YXAlog_iOS.framework/YXAlog_iOS`
    end
  end
end

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
