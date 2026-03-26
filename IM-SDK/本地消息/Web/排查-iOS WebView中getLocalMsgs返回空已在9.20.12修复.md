---
track_type: 排查类
sub_type: SDK问题
product: IM-SDK
feature: 本地消息
platform: Web
title: iOS WebView中getLocalMsgs返回空已在9.20.12修复
root_cause: iOS WebKit内核的WebView组件在处理IndexedDB时有兼容性问题，导致本地消息数据库读取返回空
solution: 升级到SDK 9.20.12版本，该版本已修复iOS WebView中getLocalMsgs返回空的问题
customers: ["香港边界科技有限公司-dx"]
source: chat_history
tags: ["getLocalMsgs","iOS WebView","9.20.12","WebKit","返回空"]
created: 2025-08-07
updated: 2026-03-26
---

## 问题：Web iOS WebView中getLocalMsgs返回空已在9.20.12修复

## 问题详情

**现象**：
iOS原生WebView中getLocalMsgs返回空数据，但在Chrome浏览器中正常

**复现步骤**：
（从会话提取；无明确步骤则省略此节）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS WebView
- 其他：iOS真机异常，模拟器正常

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. iOS WebView模拟器正常，真机异常 → 确认问题与iOS WebKit相关
2. indexedDB读写正常 → 排除数据库本身问题
3. 研发确认是iOS WebKit对数据库操作处理差异导致的 → 定位到根因

**关键发现**：iOS WebKit内核的WebView组件在处理IndexedDB时有兼容性问题，导致本地消息数据库读取返回空

## 问题原因

iOS WebKit内核的WebView组件在处理IndexedDB时有兼容性问题，导致本地消息数据库读取返回空

## 解决方案

升级到SDK 9.20.12版本，该版本已修复iOS WebView中getLocalMsgs返回空的问题

## 其他触发场景

（合并时在此处追加：`- [{platform}] {title}，来源：{customers}，{today}`）
