## 问题描述

App 启动时，应用会出现使用不流畅的情况，查看 logcat 日志 IM 相关日志频繁打印。

## 问题原因

有可能是因为频繁调用阻塞查询本地数据的接口，这类接口会查询本地数据库，如果在 UI 线程中循环调用会出现性能问题，从而导致 UI 卡顿。可以通过在 logcat 日志中过滤`TransExec: execute Transaction`关键字，确认是否有 IM 接口频繁调用的情况，尤其需要注意`xxxBlock();`这类同步方法。

## 解决方案

1. 确认是否为业务层实现有问题，通过调整业务层逻辑，避免接口频繁调用。
2. 查看 API 确认是否有批量查询的方法，避免循环调用。例如`TeamService.queryTeamBlock`可以改为`TeamService.queryTeamListBlock`。
3. 改为异步调用方法，或者放在子线程中调用，防止 UI 卡顿。