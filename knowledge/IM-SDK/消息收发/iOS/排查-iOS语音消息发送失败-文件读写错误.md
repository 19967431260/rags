---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 消息收发
platform: iOS
title: iOS语音消息发送失败-文件读写错误
root_cause: 语音文件录制未成功，没有生成有效文件，可能与AudioSession配置有关
solution: 建议业务侧在录制流程中加埋点上报，使用SDK提供的AudioSession相关方法排查录制失败原因，确认录制成功后再发送消息
customers: ["VIP云信-武汉无毁"]
source: chat_history
tags: ["语音消息", "NIMLocalErrorCodeIOError", "文件读写失败", "录制失败", "AudioSession"]
created: 2026-02-10
updated: 2026-03-15
---

## 问题：iOS iOS语音消息发送失败-文件读写错误

## 问题详情

**现象**：
用户反馈语音消息老发不出去。日志显示错误：invalid upload param，Error Domain=NIMLocalErrorDomain Code=5 "读取/写入文件失败"。文件路径：/var/mobile/Containers/Data/Application/.../d41d8cd98f00b204e9800998ecf8427e.mp3，fileExistsAtPath检查发现文件不存在。

## 排查过程

1. 检查上传日志 → 发现NIMLocalErrorCodeIOError，文件路径无效
2. 使用fileExistsAtPath检查 → 文件完全不存在
3. 确认发送前有读取数据逻辑 → 业务侧有判断文件存在
**关键发现**：错误发生在上传前，文件未成功录制生成

## 问题原因

语音文件录制未成功，没有生成有效文件，可能与AudioSession配置有关

## 解决方案

建议业务侧在录制流程中加埋点上报，使用SDK提供的AudioSession相关方法排查录制失败原因，确认录制成功后再发送消息
