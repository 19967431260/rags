---
track_type: 排查类
sub_type: 集成类
product: NERoom
feature: UI组件
platform: iOS
title: NEPitchUIKit BlocksKit库UIWebView问题
root_cause: BlocksKit第三方库已停止维护，包含未使用的UIWebView相关文件。
solution: 当前代码里已移除UIWebView相关文件，可以直接把这两个文件删除再运行。BlocksKit已停止维护，目前只能先手动避免，后续组件层面会优化。
customers: ['海南通通智能科技有限公司北京分公司']
source: chat_history
tags: ['NEPitchUIKit', 'BlocksKit', 'UIWebView', 'iOS', '审核']
created: 2025-02-20
updated: 2026-03-23
---

## 问题：iOS NEPitchUIKit BlocksKit库UIWebView问题

## 问题详情

**现象**：
NEPitchUIKit中的BlocksKit库包含UIWebView，影响App Store审核。

**环境信息**：
- 平台：iOS
- 产品：NERoom

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

（从会话提取排查过程）

## 问题原因

BlocksKit第三方库已停止维护，包含未使用的UIWebView相关文件。

## 解决方案

当前代码里已移除UIWebView相关文件，可以直接把这两个文件删除再运行。BlocksKit已停止维护，目前只能先手动避免，后续组件层面会优化。

## 其他触发场景

（合并时在此处追加：`- [iOS] NEPitchUIKit BlocksKit库UIWebView问题，来源：['海南通通智能科技有限公司北京分公司']，2026-03-23`）
