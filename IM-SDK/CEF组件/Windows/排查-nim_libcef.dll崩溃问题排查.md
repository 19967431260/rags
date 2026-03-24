---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: CEF组件
platform: Windows
title: nim_libcef.dll崩溃问题排查
root_cause: NIM_Duilib_Framework项目的CEF组件较老（2623版本），已不再维护
solution: 该Demo目前不维护，建议用比较新的CEF组件替换观察；CEF相关问题可到社区寻求协助：https://github.com/chromiumembedded/cef
customers: ['厦门市易联众易惠']
source: chat_history
tags: ['Windows', 'CEF', 'nim_libcef.dll', '崩溃', 'NIM_Duilib_Framework']
created: 2025-01-17
updated: 2026-03-23
---

## 问题：Windows nim_libcef.dll崩溃问题排查

## 问题详情

**现象**：
客户使用PC版本的nim_libcef.dll（2623版本，支持XP的最后一个版本），在Win10系统上运行时会偶现崩溃，每天24小时运行过程中会出现1-2次。

## 排查过程

1. 客户反馈nim_libcef.dll偶现崩溃，提供dump文件
2. 询问SDK版本、设备配置、崩溃频率
3. 客户使用2623版本，支持XP的最后一个版本，运行在Win10系统
4. 崩溃为多设备偶现，每天1-2次
5. 客户之前使用cef_76版本但C++往web发送JS事件会白屏
6. 建议客户提供SDK日志
7. 客户反馈使用的是nim_libcef.dll，找不到日志
8. 转研发查看，研发反馈nim_libcef.dll是上层程序层，没有IM和NERTC的SDK加载，无法解析堆栈
9. 客户确认nim_libcef.dll是网易云CEF重新封装的DLL
10. 研发确认该Demo目前不维护，建议用比较新的CEF组件替换

## 问题原因

NIM_Duilib_Framework项目的CEF组件较老（2623版本），已不再维护

## 解决方案

该Demo目前不维护，建议用比较新的CEF组件替换观察；CEF相关问题可到社区寻求协助：https://github.com/chromiumembedded/cef

## 其他触发场景

（合并时在此处追加）
