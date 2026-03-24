---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 推送
platform: Uniapp
title: 荣耀手机SDK未初始化闪退
root_cause: 荣耀推送插件版本过旧，需要升级到1.1.2版本
solution: 升级荣耀推送插件到1.1.2版本，参考文档：https://doc.yunxin.163.com/messaging/guide/DQ1NTAxNzI?platform=uniapp
customers: ['北京集藏科技有限公司']
source: chat_history
tags: ['荣耀', '闪退', 'SDK未初始化', '推送插件', '1.1.2', 'Uniapp']
created: 2025-01-18
updated: 2026-03-23
---

## 问题：Uniapp 荣耀手机SDK未初始化闪退

## 问题详情

**现象**：
客户使用IM V10 Uniapp版本，在荣耀手机上出现闪退，报错：SDK not initialized, call NimClient.init() first!

## 排查过程

1. 检查manifest.json中PUSH_HONOR_APPID配置 → 已配置\n2. 检查推送插件版本 → 发现版本过旧\n3. 建议升级到1.1.2版本

## 问题原因

荣耀推送插件版本过旧，需要升级到1.1.2版本

## 解决方案

升级荣耀推送插件到1.1.2版本，参考文档：https://doc.yunxin.163.com/messaging/guide/DQ1NTAxNzI?platform=uniapp

## 其他触发场景

（合并时在此处追加）
