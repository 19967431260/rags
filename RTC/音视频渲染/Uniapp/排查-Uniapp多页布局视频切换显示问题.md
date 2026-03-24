---
track_type: 排查类
sub_type: 使用问题
product: RTC
feature: 音视频渲染
platform: Uniapp
title: Uniapp多页布局视频切换显示问题
root_cause: 使用swiper组件实现多页面渲染，每次点击视频调整swiper页面视频渲染画面时，不方便手动destroy之前设置的视图canvas
solution: 1. 调整multiCall.nvue代码逻辑，在@onViewLoad回调事件中设置画布
2. iOS端原生插件支持覆盖之前设置的视图canvas
3. 升级到5.6.35版本
customers: ['VIP云信-雨后生活服务（杭州）']
source: chat_history
tags: ['RTC', 'Uniapp', '多页布局', '视频渲染', 'swiper', '画布']
created: 2025-02-05
updated: 2026-03-23
---

## 问题：Uniapp Uniapp多页布局视频切换显示问题

## 问题详情

**现象**：
客户使用uniapp开发多人视频通话，使用swiper组件实现多页面渲染视图。点击放大后当前页布局数量减少，有些视频跑到第二页，切换到第二页时对端视频和本地视频都不显示。安卓切换到第二页远程视频可以，自己的不行；iOS都不行。

**环境信息**：
- 平台：Uniapp
- 产品：RTC

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 客户提供示例代码和视频
2. 研发分析是视频画布设置问题
3. 调整multiCall.nvue的用户代码逻辑，主要是设置视频画布方面（@onViewLoad回调事件）
4. 修改iOS端原生插件支持覆盖之前设置的视图canvas
5. 建议升级到5.6.35版本使用onViewLoad事件

## 问题原因

使用swiper组件实现多页面渲染，每次点击视频调整swiper页面视频渲染画面时，不方便手动destroy之前设置的视图canvas

## 解决方案

1. 调整multiCall.nvue代码逻辑，在@onViewLoad回调事件中设置画布
2. iOS端原生插件支持覆盖之前设置的视图canvas
3. 升级到5.6.35版本

## 其他触发场景

（合并时在此处追加：`- [Uniapp] Uniapp多页布局视频切换显示问题，来源：['VIP云信-雨后生活服务（杭州）']，2026-03-23`）
