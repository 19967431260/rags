# Playbook: 利用 IM 日志拉取能力并带上传 RTC/呼叫组件日志

## 目标
当客户已经接入 **IM 日志拉取**，但排障还缺少 RTC 或呼叫组件日志时，可以通过把这些日志统一放到 IM 缓存目录下的 `extra_log` 中，随着 IM 日志拉取一起上传，减少客户重复取日志的成本。

这是一份 **能力建设型 playbook**，适合指导客户/研发改代码、发下一版，而不是直接用于判断某一次线上故障根因。

## 适用前提
- 客户 App 已接入 IM SDK，并具备 IM 日志拉取能力。
- 客户愿意调整本地日志目录配置。
- 需要补齐的日志包括 RTC SDK 或呼叫组件日志。

## 核心原理
IM 在初始化时可指定缓存根目录 `SDKOptions.sdkStorageRootPath`。
当使用 IM 的日志拉取功能时，会把该目录下的 **`extra_log`** 文件夹一并打包上传。

因此，关键动作就是：
1. 先把 IM 缓存目录设到应用可写私有目录。
2. 再把 RTC / 呼叫组件日志目录都指向 `.../nim/extra_log`。

## 实施步骤

### 步骤 1：确认 IM 缓存根目录
示例：
```java
SDKOptions options = new SDKOptions();
options.sdkStorageRootPath = context.getExternalFilesDir().getAbsolutePath() + "/nim";
NIMClient.init(context, null, options);
```

**要点**
- 文档明确提醒：高版本 Android 上应使用应用私有目录，否则可能没有写权限。
- 如果 IM 根目录不是这里，后续 `extra_log` 路径也要跟着调整。

### 步骤 2：把 RTC 日志写入 extra_log
示例：
```java
NERtcOption neRtcOption = new NERtcOption();
neRtcOption.logDir = context.getExternalFilesDir().getAbsolutePath() + "/nim/extra_log";
NERtcEx.getInstance().init(context, appKey, callback, neRtcOption);
```

**完成后效果**
- RTC 日志会落到 IM 可打包的附加日志目录中。

### 步骤 3：按呼叫组件版本分别处理

#### 方案 A：呼叫组件 V1.8.2 及以上
1. 实现 `XKitInitOptions`，把组件日志路径设到 `extra_log`：
```java
@Keep
public class ExampleOptions implements XKitInitOptions {
  @Nullable
  @Override
  public logOption(@NonNull Context context) {
    return new XKitLogOptions.Builder()
      .path(context.getExternalFilesDir().getAbsolutePath() + "/nim/extra_log")
      .build();
  }
}
```
2. 在 `AndroidManifest` 注册：
```xml
<meta-data
    android:name="XKitInitOptions 子类的全类名"
    android:value="com.netease.yunxin.xkit.options" />
```
3. 若使用呼叫组件承接 RTC 初始化，则把 RTC 日志路径也通过呼叫组件初始化配置传入：
```java
NERtcOption neRtcOption = new NERtcOption();
neRtcOption.logDir = getExternalFilesDir().getAbsolutePath() + "/nim/extra_log";

CallKitUIOptions options = new CallKitUIOptions.Builder()
    .rtcSdkOption(neRtcOption)
    .build();
CallKitUI.init(getApplicationContext(), options);
```

#### 方案 B：呼叫组件 V1.3.3 ~ V1.8
需在初始化时同时设置：
- RTC 日志目录
- 呼叫组件日志根目录

示例：
```java
NERtcOption neRtcOption = new NERtcOption();
neRtcOption.logDir = context.getExternalFilesDir().getAbsolutePath() + "/nim/extra_log";

CallKitUIOptions options = new CallKitUIOptions.Builder()
    .rtcSdkOption(neRtcOption)
    .logRootPath(neRtcOption.logDir)
    .build();
CallKitUI.init(getApplicationContext(), options);
```

## 给主 skill 的落地用法
当用户说：
- “IM 日志拉到了，但没有 RTC 日志。”
- “能不能一次把多个产品日志都拉上来？”
- “想让客户下个版本补充日志采集能力。”

主 skill 可以这样使用本 playbook：
1. 先确认客户接入的产品：IM / RTC / 呼叫组件。
2. 再确认版本区间，尤其是呼叫组件版本是否 `>= 1.8.2`。
3. 给出对应配置片段，让客户研发在下一版接入。
4. 明确预期：**这是为了后续更高效取证，不是对当前已发生问题的即时补救。**

## 诊断价值边界
这份文档解决的是“以后怎么把日志收上来”，不是“现在这次故障为什么发生”。
因此它适合放在：
- 补日志采集建议
- 客户侧接入整改建议
- 下一版排障能力建设

不适合放在：
- 直接根因判断
- 已有日志情况下的现象解释

## 风险与注意事项
- 来源于个人草稿，执行前建议结合当前 SDK 文档/版本核验类名与初始化方式。
- 路径依赖 Android 私有目录；若客户做了自定义存储封装，需按实际路径改写。
- 若客户版本跨度大，必须先确认呼叫组件版本区间再给配置方案。
