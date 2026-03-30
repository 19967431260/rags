---
track_type: 排查类
sub_type: 使用问题
product: IM-SDK
feature: 会话未读数
platform: Android
title: clearUnreadCountByIds清除未读数失败
root_cause: SDK内部多线程并发问题，收到新消息触发未读数+1和调用clearUnreadCountByIds清除未读数两个操作时间过于接近，导致内存缓存未正确同步，虽然数据库已清零但查询接口返回的内存缓存数据仍为旧值。
solution: 临时方案：在清除未读数逻辑中增加1秒延迟，避免极限时序触发并发问题。或使用onConversationChanged回调中的会话对象未读数（但测试发现该方案也存在问题）。根本解决需等待SDK后续版本修复，版本周期约1个月。无法手动修改未读数，只能等待官方修复。
customers: ["上海数悦信息科技有限公司"]
source: chat_history
tags: ["clearUnreadCountByIds", "未读数", "多线程", "缓存同步", "Android", "10.9.75"]
created: 2026-02-27
updated: 2026-03-17
---

## 问题：Android clearUnreadCountByIds清除未读数失败

## 问题详情

**现象**：
Android端SDK版本10.9.75，在会话界面收到消息瞬间关闭页面调用clearUnreadCountByIds方法清除未读数时，偶现未读数无法清除。UI显示未读数为1，但重启app后未读数恢复为0。在Fragment的onPause()方法中调用清除逻辑，收到消息立即手动触发onPause时复现概率非常高。

**环境信息**：
- SDK 版本：10.9.75
- 平台：Android
- 复现场景：Fragment onPause()中调用clearUnreadCountByIds，收到消息立即触发

## 排查过程

1. 检查调用时机 → 在Fragment onPause()中调用clearUnreadCountByIds
2. 查看SDK日志 → 日志显示clearUnreadCountByIds调用成功，数据库未读数为0
3. 检查UI数据源 → UI层查询的是内存缓存数据，显示为1
4. 分析时序 → 收到消息后立即调用清除，两个操作时间非常接近
5. 检查数据库 → 数据库中未读数已正确清零

**关键发现**：SDK内存缓存未正确更新，数据库已清零但内存缓存仍为1，是多线程操作同一对象导致的并发问题。

## 问题原因

SDK内部多线程并发问题，收到新消息触发未读数+1和调用clearUnreadCountByIds清除未读数两个操作时间过于接近，导致内存缓存未正确同步，虽然数据库已清零但查询接口返回的内存缓存数据仍为旧值。

## 解决方案

临时方案：在清除未读数逻辑中增加1秒延迟，避免极限时序触发并发问题。或使用onConversationChanged回调中的会话对象未读数（但测试发现该方案也存在问题）。根本解决需等待SDK后续版本修复，版本周期约1个月。无法手动修改未读数，只能等待官方修复。

## 其他触发场景
