---
track_type: 排查类
sub_type: 使用问题
product: IM-UIKit
feature: 组件-底层SDK交互
platform: Web
title: Web端输入框输入触发ChatContainer重新渲染
root_cause: UIKit组件设计机制导致输入框状态变更时会触发整体渲染
solution: 使用mobx的autorun方法监听会话变更，在onMount中通过js API控制自定义按钮显示/隐藏，避免在渲染方法中直接调用接口。代码参考：import { autorun } from 'mobx'; 在onMount中监听会话变化并执行异步请求。
customers: ['深圳中兴网信科技有限公司']
source: chat_history
tags: ['IM-UIKit', 'Web', 'ChatContainer', '重新渲染', 'autorun', 'mobx']
created: 2025-01-13
updated: 2026-03-23
---

## 问题：Web端输入框输入触发ChatContainer重新渲染

## 问题详情

**现象**：
客户在使用IM V9 UIKit Web端时，发现每次在输入框输入内容都会触发ChatContainer组件重新渲染，导致自定义按钮的接口调用过于频繁。客户希望在切换聊天人时才触发一次接口调用，而不是每次输入都触发。

## 排查过程

1. 客户反馈输入框输入时触发ChatContainer渲染方法执行
2. 技术支持建议通过autorun监听会话变更，异步请求后通过js控制隐藏
3. 客户尝试后autorun方法报错，需要安装mobx插件
4. 最终通过import { autorun } from 'mobx'解决问题

## 问题原因

UIKit组件设计机制导致输入框状态变更时会触发整体渲染

## 解决方案

使用mobx的autorun方法监听会话变更，在onMount中通过js API控制自定义按钮显示/隐藏，避免在渲染方法中直接调用接口。代码参考：import { autorun } from 'mobx'; 在onMount中监听会话变化并执行异步请求。

## 其他触发场景

（合并时在此处追加）
