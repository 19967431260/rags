---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: Bitcode
platform: iOS
title: iOS SDK移除Bitcode后仍报包含Bitcode问题
root_cause: IM SDK包含多个framework，需要全部移除bitcode。RTC有批量移除脚本，但YXAlog需要手动处理。
solution: 需要移除所有SDK framework的bitcode。RTC可使用remove_nertc_bitcode.sh脚本批量处理，YXAlog需要手动执行：xcrun bitcode_strip -r YXAlog_iOS -o YXAlog_iOS。参考文档：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client
customers: ['达济中道(沈阳)信息科技']
source: chat_history
tags: ['IM-SDK', 'iOS', 'Bitcode', 'YXAlog', '打包', 'App Store']
created: 2025-01-14
updated: 2026-03-23
---

## 问题：iOS iOS SDK移除Bitcode后仍报包含Bitcode问题

## 问题详情

**现象**：
客户按照文档移除Bitcode后，打包时仍提示SDK包含Bitcode。

## 排查过程

1. 确认移除方式 → 客户使用脚本移除
2. 检查所有framework → 确认所有SDK framework都已处理
3. 发现遗漏 → YXAlog未处理
4. 提供方案 → 手动去除YXAlog的bitcode
5. 执行命令 → xcrun bitcode_strip -r YXAlog_iOS -o YXAlog_iOS

## 问题原因

IM SDK包含多个framework，需要全部移除bitcode。RTC有批量移除脚本，但YXAlog需要手动处理。

## 解决方案

需要移除所有SDK framework的bitcode。RTC可使用remove_nertc_bitcode.sh脚本批量处理，YXAlog需要手动执行：xcrun bitcode_strip -r YXAlog_iOS -o YXAlog_iOS。参考文档：https://doc.yunxin.163.com/messaging2/faq/jE4MjAwMTI?platform=client

## 其他触发场景

（合并时在此处追加）
