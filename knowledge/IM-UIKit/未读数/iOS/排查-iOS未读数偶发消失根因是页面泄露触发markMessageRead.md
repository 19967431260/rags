---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 未读数
platform: iOS
title: iOS未读数偶发消失根因是页面泄露触发markMessageRead
root_cause: 页面泄露导致UIViewController未正确释放，返回时意外进入消息详情页触发了markMessageRead清未读；UIKit本身不会自动联动
solution: iOS未读数偶发清零排查方法：在所有markMessageRead调用处加弹窗日志确认触发时机；根因通常是页面泄露导致视图控制器在后台未释放，切换回来时意外进入消息详情触发已读；解决页面泄露问题（检查navigationController栈管理）
customers: ["江苏新汇奥信息科技有限公司"]
source: chat_history
tags: ["iOS","未读数","markMessageRead","页面泄露","UIKit"]
created: 2025-08-25
updated: 2026-03-26
---

## 问题：iOS iOS未读数偶发消失根因是页面泄露触发markMessageRead

## 问题详情

**现象**：
iOS App杀掉后重新进入，消息未读数偶发为0；客户未手动调用markMessageRead但日志显示被调用了。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：iOS
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供app切入后台再切前台未读数偶发消失 → 确认问题
2. 客服查日志确认是markMessageRead被调用了 → 定位调用
3. 客户提供录屏确认退出后未读消失 → 确认复现
4. 研发分析：可能是页面泄露导致返回时意外触发进入消息详情 → 根因推测
5. 建议：解决页面泄露问题，在markMessageRead调用处加弹窗确认触发时机 → 排查方案

**关键发现**：页面泄露导致UIViewController未正确释放，返回时意外进入消息详情页触发了markMessageRead清未读；UIKit本身不会自动联动

## 问题原因

页面泄露导致UIViewController未正确释放，返回时意外进入消息详情页触发了markMessageRead清未读；UIKit本身不会自动联动。

## 解决方案

iOS未读数偶发清零排查方法：在所有markMessageRead调用处加弹窗日志确认触发时机；根因通常是页面泄露导致视图控制器在后台未释放，切换回来时意外进入消息详情触发已读；解决页面泄露问题（检查navigationController栈管理）。

## 其他触发场景

（合并时在此处追加）
