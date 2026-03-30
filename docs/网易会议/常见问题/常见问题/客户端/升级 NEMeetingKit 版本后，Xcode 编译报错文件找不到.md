## 问题描述

从网易会议组件（NEMeetingKit）4.12.0 之前的版本升级后，Xcode 编译报错 `'NEMeetingKit/NEMeetingKit.h' file not found`。

## 原因分析

为了符合 Apple 的新的上架规则，NEMeetingKit 自 4.12.0 版本起，将由 XCFramework 框架形式提供动态库。您在集成 [iOS 版](https://doc.yunxin.163.com/meeting/guide/zg0NTkxMjY?platform=iOS) 及 [macOS 版](https://doc.yunxin.163.com/meeting/guide/DQzNDg3NDU?platform=pc) NEMeetingKit 时引入的 `.framework` 文件更名为 `.xcframework` 格式，因此在升级时，会报错 `'NEMeetingKit/NEMeetingKit.h' file not found`。

XCFramework 是 Apple 在 Xcode 11 中引入的一种新的框架格式，它包含了 framework 或 library 的一个或多个变体，用于简化和优化在不同平台（如 iOS、macOS、watchOS 和 tvOS）上使用的二进制库的管理和分发。XCFramework 是一种相对 Framework 更便捷的格式。

## 解决方案

如果您的 iOS 或 macOS 应用项目中曾集成过低于 4.12.0 版本的 NEMeetingKit，升级 SDK 至 4.12.0 及以上版本的同时，请需要检查以下几个部分：

1. 升级到最新版本的 Xcode。

2. 如果您是通过 Cocoapods 进行集成，请确保 Cocoapods 版本高于 1.9.0（建议更新至 1.10.0 以上）。更新后，删除 `Podfile.lock` 文件，并再次执行 `pod install` 操作。

3. 在 Xcode 中，通过 Shift(⇧)+Command(⌘)+K 的组合快捷键或者 Product > Clean 对项目执行清除缓存操作，并再次编译项目。