---
track_type: 排查类
sub_type: 集成类
product: IM-SDK
feature: CocoaPods集成
platform: iOS
title: use_frameworks!与项目库冲突解决方案
root_cause: 项目原有库(libextobjc等)不支持use_frameworks!动态框架
solution: 在Podfile中添加pre_install脚本，将特定库强制指定为动态框架：
pre_install do |installer|
  $dynamic_frameworks = ['libextobjc']
  installer.pod_targets.each do |pod|
    if $dynamic_frameworks.include?(pod.name)
      def pod.build_type;
        BuildType.new(:linkage => :dynamic, :packaging => :framework)
      end
    end
  end
end
customers: ['通通派对']
source: chat_history
tags: ['use_frameworks!', 'CocoaPods', 'libextobjc', '动态框架', '集成冲突']
created: 2025-01-10
updated: 2026-03-23
---

## 问题：use_frameworks!与项目库冲突解决方案

## 问题详情

**现象**：
集成IM SDK需要use_frameworks!，但与项目原有库冲突，原库不支持use_frameworks!且找不到维护人员。

## 排查过程

1. 建议优先升级原有库支持use_frameworks!
2. 如无法升级，提供pre_install脚本方案

## 问题原因

项目原有库(libextobjc等)不支持use_frameworks!动态框架

## 解决方案

在Podfile中添加pre_install脚本，将特定库强制指定为动态框架：
pre_install do |installer|
  $dynamic_frameworks = ['libextobjc']
  installer.pod_targets.each do |pod|
    if $dynamic_frameworks.include?(pod.name)
      def pod.build_type;
        BuildType.new(:linkage => :dynamic, :packaging => :framework)
      end
    end
  end
end

## 其他触发场景

（合并时在此处追加）
