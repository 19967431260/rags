---
track_type: 排查类
sub_type: BUG问题
product: IM V10
feature: Unity集成
platform: iOS
title: Unity V10 iOS打包后闪退问题
root_cause: nim_audio库默认没有勾选Embedded binaries导入方式，导致启动时找不到动态库而闪退
solution: 将nim_audio以Embedded binaries形式导入。下载的package导入时，nim_audio默认没勾选Embedded binaries，需要手动勾选。
customers: ["北京久幺幺"]
source: chat_history
tags: ["Unity", "iOS", "闪退", "Embedded binaries", "nim_audio"]
created: 2026-01-15
updated: 2026-03-15
---

## 问题：iOS Unity V10 iOS打包后闪退问题

## 问题详情

**现象**：
客户导入最新Unity客户端package（nim-unity-universal-2-10-2-30-build-3350941），编辑器下运行正常，但Xcode打包后一运行就闪退，连APP闪屏阶段都没到。之前低版本没问题，升级到新版本才出现。

## 排查过程

1. 检查是否有崩溃堆栈 2. 在手机设置-隐私-分析与改进-分析数据中导出崩溃日志 3. 检查nim_audio库的导入方式

## 问题原因

nim_audio库默认没有勾选Embedded binaries导入方式，导致启动时找不到动态库而闪退

## 解决方案

将nim_audio以Embedded binaries形式导入。下载的package导入时，nim_audio默认没勾选Embedded binaries，需要手动勾选。

## 其他触发场景

（合并时在此处追加）
