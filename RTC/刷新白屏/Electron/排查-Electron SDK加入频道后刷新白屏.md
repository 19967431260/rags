---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 刷新白屏
platform: Electron
title: Electron SDK加入频道后刷新白屏
root_cause: 初步判断为Electron内核刷新机制与SDK初始化后的资源释放问题。
solution: Electron SDK加入频道后刷新白屏问题，初步判断为Electron内核机制问题，建议研发进一步排查SDK资源释放逻辑。临时方案：避免刷新或使用编辑器保存触发刷新。
customers: ['西安美电智能科技有限公司']
source: chat_history
tags: ['Electron', '白屏', '刷新', 'RTC']
created: 2025-02-21
updated: 2026-03-23
---

## 问题：Electron Electron SDK加入频道后刷新白屏

## 问题详情

**现象**：
Electron端加入频道后刷新页面出现白屏，不加入频道刷新正常。

**环境信息**：
- 平台：Electron
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 确认复现条件 → 加入频道后刷新100%复现
2. 测试demo → 同样复现
3. 测试编辑器刷新 → 正常
4. 初步判断 → Electron内核刷新机制问题
5. 建议 → 研发进一步排查

## 问题原因

初步判断为Electron内核刷新机制与SDK初始化后的资源释放问题。

## 解决方案

Electron SDK加入频道后刷新白屏问题，初步判断为Electron内核机制问题，建议研发进一步排查SDK资源释放逻辑。临时方案：避免刷新或使用编辑器保存触发刷新。

## 其他触发场景

（合并时在此处追加：`- [Electron] Electron SDK加入频道后刷新白屏，来源：['西安美电智能科技有限公司']，2026-03-23`）
