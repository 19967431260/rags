---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: Uniapp
platform: Uniapp
title: UniApp Uikit重启后会话列表为空：无本地DB，依赖漫游，建议升级高级版云端会话
root_cause: UniApp Uikit没有本地DB，每次登录只能依赖漫游生成会话列表；标准版漫游只有3天/50会话/50条
solution: 建议升级高级版开通云端会话（有效期1年，1000会话），由服务器维护会话列表；或者开启漫游（标准版有3天漫游时效）
customers: ["世达工具（上海）"]
source: chat_history
tags: ["Uniapp", "Uikit", "会话列表", "漫游", "云端会话", "高级版"]
created: 2025-07-09
updated: 2026-03-25
---

## 问题：UniApp Uikit重启后会话列表为空：无本地DB，依赖漫游，建议升级高级版云端会话

## 问题原因

UniApp Uikit没有本地DB，每次登录只能依赖漫游生成会话列表；标准版漫游只有3天/50会话/50条

## 解决方案

建议升级高级版开通云端会话（有效期1年，1000会话），由服务器维护会话列表；或者开启漫游（标准版有3天漫游时效）
