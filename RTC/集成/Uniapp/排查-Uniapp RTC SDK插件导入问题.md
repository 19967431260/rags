---
track_type: 排查类
sub_type: 集成类
product: RTC
feature: 集成
platform: Uniapp
title: Uniapp RTC SDK插件导入问题
root_cause: 文档有误，RTC插件目前未上架DCloud插件市场。
solution: 两个SDK（原生插件和JS封装层）都导入成功后即可自定义基座打包。文档中关于插件市场的步骤有误，目前插件未上架应用市场，直接导入SDK即可。
customers: ['杭州奇偶网络科技有限公司']
source: chat_history
tags: ['Uniapp', 'RTC', '插件', '集成', 'JS封装层']
created: 2025-02-10
updated: 2026-03-23
---

## 问题：Uniapp Uniapp RTC SDK插件导入问题

## 问题详情

**现象**：
按照文档导入Uniapp JS封装层插件时遇到问题，文档中提到的插件市场步骤看不懂。

**环境信息**：
- 平台：Uniapp
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

文档有误，RTC插件目前未上架DCloud插件市场。

## 解决方案

两个SDK（原生插件和JS封装层）都导入成功后即可自定义基座打包。文档中关于插件市场的步骤有误，目前插件未上架应用市场，直接导入SDK即可。

## 其他触发场景

（合并时在此处追加：`- [Uniapp] Uniapp RTC SDK插件导入问题，来源：['杭州奇偶网络科技有限公司']，2026-03-23`）
