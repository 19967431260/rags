---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 组件使用
platform: Web
title: Web端V9切换账号实现方法
root_cause: UIKit没有单独处理直接切换账号的逻辑，需要正确销毁NIM实例和store，并延迟后重新初始化。
solution: 切换账号时：1. 调用nim.disconnect()断开连接；2. 调用store.destroy()销毁store；3. 延迟1秒后重新初始化。参考Vue切换示例代码。
customers: ['北京新流通信息科技有限公司']
source: chat_history
tags: ['IM-UIKit', 'Web', 'V9', '切换账号', 'destroy']
created: 2025-02-18
updated: 2026-03-23
---

## 问题：Web Web端V9切换账号实现方法

## 问题详情

**现象**：
客户使用Web端V9 UIKit，需要实现切换账号功能，但不知道如何正确销毁和重新初始化。

**环境信息**：
- 平台：Web
- 产品：IM-UIKit

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户尝试销毁后重新初始化 → 切换后没数据
2. 使用window.__xkit_store__.store.connectstore.destroy() → 未完全销毁
3. 使用window.__xkit_store__.store.connectStore.nim.destroy() → 仍有问题
4. 使用const { store, nim } = uikit.getStateContext(); nim.disconnect(); store.destroy(); → 成功

## 问题原因

UIKit没有单独处理直接切换账号的逻辑，需要正确销毁NIM实例和store，并延迟后重新初始化。

## 解决方案

切换账号时：1. 调用nim.disconnect()断开连接；2. 调用store.destroy()销毁store；3. 延迟1秒后重新初始化。参考Vue切换示例代码。

## 其他触发场景

（合并时在此处追加：`- [Web] Web端V9切换账号实现方法，来源：['北京新流通信息科技有限公司']，2026-03-23`）
