---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: 登录状态
platform: Android
title: 网络断开恢复后observeOnlineStatus无回调
root_cause: SDK自动重连失败后Auth会话失效，如果业务层主动调用login接口，SDK直接在login回调中返回失败，不会触发observeOnlineStatus回调和后续重连
solution: 登录成功后将重连逻辑托管给SDK：1. 不要在SDK登录成功后重复手动调用login接口 2. 通过AuthServiceObserver.observeDataReady监听数据库就绪事件 3. 收到NET_BROKEN后等待网络恢复，SDK会自动探测并重连 4. 如需自行维护登录逻辑，需记录登录错误并在网络恢复后调用login
customers: ["极之客-dx"]
source: chat_history
tags: ["observeOnlineStatus","重连","NET_BROKEN","登录状态","自动重连","Auth会话"]
created: 2025-08-13
updated: 2026-03-26
---

## 问题：Android 网络断开恢复后observeOnlineStatus无回调

## 问题详情

**现象**：
Android端用户网络断开后observeOnlineStatus回调正常变为NET_BROKEN，但网络恢复后没有收到任何回调。约1分钟后重试了10次后SDK不再尝试重连。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：（从会话提取，无则省略）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 拉取SDK日志确认SDK确实没有回调 → 确认问题
2. 发现日志显示do user manual login（主动调用了login接口）→ 定位触发条件
3. 客服确认：SDK长连接自动重连失败后会话失效，此时如果业务层手动调用login接口，SDK不会触发重连流程 → 根因确认

**关键发现**：SDK自动重连失败后Auth会话失效，如果业务层主动调用login接口，SDK直接在login回调中返回失败，不会触发observeOnlineStatus回调和后续重连

## 问题原因

SDK自动重连失败后Auth会话失效，如果业务层主动调用login接口，SDK直接在login回调中返回失败，不会触发observeOnlineStatus回调和后续重连。

## 解决方案

登录成功后将重连逻辑托管给SDK：1. 不要在SDK登录成功后重复手动调用login接口 2. 通过AuthServiceObserver.observeDataReady监听数据库就绪事件 3. 收到NET_BROKEN后等待网络恢复，SDK会自动探测并重连 4. 如需自行维护登录逻辑，需记录登录错误并在网络恢复后调用login。

## 其他触发场景

（合并时在此处追加）
