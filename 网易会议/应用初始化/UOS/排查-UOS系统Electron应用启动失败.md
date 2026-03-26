---
track_type: 排查类
sub_type: 环境兼容类
product: 网易会议
feature: 应用初始化
platform: UOS
title: UOS系统Electron应用启动失败
root_cause: UOS系统Electron缺少必要的系统库支持，且沙盒权限配置导致主进程无法正常初始化
solution: 在应用入口（app.on('ready')之前）添加以下配置：if (process.platform === 'linux' && os.arch() === 'arm64') { app.disableHardwareAcceleration(); app.commandLine.appendSwitch('--no-sandbox'); app.commandLine.appendSwitch('--in-process-gpu'); app.commandLine.appendSwitch('--disable-gpu'); app.commandLine.appendSwitch('--disable-software-rasterizer'); }
customers: ["四川掌安安全科技有限公司"]
source: chat_history
tags: ["UOS","ARM","Electron","启动失败","沙盒","硬件加速"]
created: 2025-08-12
updated: 2026-03-26
---

## 问题：UOS UOS系统Electron应用启动失败

## 问题详情

**现象**：
UOS系统（ARM架构）上Electron应用无法启动，本地开发模式正常，但打包后运行不起来，提示无法执行二进制文件。

**复现步骤**：
（无明确步骤，从会话提取）

**环境信息**：
- SDK 版本：（从会话提取，无则省略）
- 系统版本 / 设备：UOS（ARM架构）
- 其他：（网络环境、账号类型等，无则省略）

**相关日志**：
（从会话提取关键报错日志，无则省略）

## 排查过程

1. 远程排查确认主进程未正常启动 → 确认问题
2. 发现沙盒权限问题 → 定位问题
3. 需要禁用硬件加速和相关GPU参数 → 解决方案

**关键发现**：UOS系统Electron缺少必要的系统库支持，且沙盒权限配置导致主进程无法正常初始化

## 问题原因

UOS系统Electron缺少必要的系统库支持，且沙盒权限配置导致主进程无法正常初始化。

## 解决方案

在应用入口（app.on('ready')之前）添加以下配置：
```javascript
if (process.platform === 'linux' && os.arch() === 'arm64') {
    app.disableHardwareAcceleration();
    app.commandLine.appendSwitch('--no-sandbox');
    app.commandLine.appendSwitch('--in-process-gpu');
    app.commandLine.appendSwitch('--disable-gpu');
    app.commandLine.appendSwitch('--disable-software-rasterizer');
}
```

## 其他触发场景

（合并时在此处追加）
