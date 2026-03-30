---
track_type: 排查类
sub_type: 使用问题
product: NERoom
feature: 音频共享
platform: Android
title: Android enableLoopbackRecording音频共享无声音
root_cause: 音频共享功能需要ScreenShareService前台服务支持，但Flutter层无法直接启动Android原生服务，需要客户在原生层处理。
solution: 1. 临时方案：使用startAudioMixing接口播放本地音频文件实现伴音功能
2. 参考文档：https://doc.yunxin.163.com/neroom/guide/TM0MjUzMjQ?platform=android
3. 如需enableLoopbackRecording，需在Android原生层启动ScreenShareService前台服务
4. 注意：模拟器不支持，仅真机可用
customers: ["海南探寻未来科技有限责任公司"]
source: chat_history
tags: ["enableLoopbackRecording", "音频共享", "无声音", "ScreenShareService", "Flutter", "伴音"]
created: 2025-11-10
updated: 2026-03-20
---

## 问题：Android Android enableLoopbackRecording音频共享无声音

## 问题详情

**现象**：
客户需要在语聊房中实现音频共享功能（如播放网易云音乐共享给对方）。使用enableLoopbackRecording接口返回值是0，但对方听不到音乐声音。

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认接口调用 → enableLoopbackRecording返回0，但无声音
2. 检查ScreenShareService → 客户未正确添加前台服务
3. 提供Service实现代码 → 客户添加后仍无法进入断点
4. 分析实现方式 → 发现音频共享依赖屏幕共享的前台服务
5. 提供替代方案 → 建议通过startAudioMixing播放本地音频文件
**关键发现**：enableLoopbackRecording需要ScreenShareService前台服务支持，但Flutter层无法直接启动Android原生服务

**关键发现**：

## 问题原因

音频共享功能需要ScreenShareService前台服务支持，但Flutter层无法直接启动Android原生服务，需要客户在原生层处理。

## 解决方案

1. 临时方案：使用startAudioMixing接口播放本地音频文件实现伴音功能
2. 参考文档：https://doc.yunxin.163.com/neroom/guide/TM0MjUzMjQ?platform=android
3. 如需enableLoopbackRecording，需在Android原生层启动ScreenShareService前台服务
4. 注意：模拟器不支持，仅真机可用

## 其他触发场景

