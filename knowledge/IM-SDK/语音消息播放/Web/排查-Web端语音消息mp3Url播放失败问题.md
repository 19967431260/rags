---
track_type: "排查类"
sub_type: "使用问题"
product: "IM-SDK"
feature: "语音消息播放"
platform: "Web"
title: "Web端语音消息mp3Url播放失败问题"
root_cause: "Web SDK对ext为mp3的语音消息自动拼接audioTrans&type=mp3参数，但本身就是mp3格式不需要转码"
solution: "ext为mp3时取url字段，不为mp3时取mp3Url字段；不要无脑取url，否则可能Web播放不出来"
customers: ["智己"]
source: "chat_history"
tags: ["语音消息", "mp3", "Web", "audioTrans", "播放失败"]
created: "2025-09-29"
updated: "2026-03-20"
---

## 问题：Web Web端语音消息mp3Url播放失败问题

## 问题详情

**现象**：
用户发送的语音/mp3消息播放不了，控制台报错；去掉URL参数?audioTrans&type=mp3后能正常播放

## 排查过程

1. 分析问题现象 → mp3格式语音消息播放失败
2. 对比测试 → 去掉audioTrans参数后可播放
3. 排查数据来源 → 确认云端历史消息不带audioTrans参数
4. 定位问题 → Web SDK自行拼接mp3Url，ext为mp3时不需要转码
**关键发现**：Web SDK对mp3格式语音自动拼接转码参数导致问题

## 问题原因

Web SDK对ext为mp3的语音消息自动拼接audioTrans&type=mp3参数，但本身就是mp3格式不需要转码

## 解决方案

ext为mp3时取url字段，不为mp3时取mp3Url字段；不要无脑取url，否则可能Web播放不出来

## 其他触发场景
