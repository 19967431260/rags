## 问题现象

当应用的 targetSDK=34 (Android 14) 时，启动 [屏幕共享](https://doc.yunxin.163.com/nertc/guide/jk4MjIzMTY?platform=android) 功能可能会出现应用崩溃，并在日志中显示以下错误：

```
Caused by: java.lang.SecurityException: Starting FGS with type mediaProjection callerApp=ProcessRecord {647993 9353: com.xxxx.xxxx.xxxx/u0a212} targetSDK=34 requires permissions: all of the permissions all0f=true [android. permission.FOREGROUND_SERVICE_MEDIA_PROJECTION] any of the permissions a110=false [android.permission.CAPTURE_VIDEO_OUTPUT, android:project_media]
```

## 问题原因

Android 14 对前台服务和媒体投射权限进行了安全增强。具体来说：

1. Android 14 要求使用媒体投射的前台服务时，必须声明 `FOREGROUND_SERVICE_MEDIA_PROJECTION` 权限。
2. 必须先获取屏幕共享权限，再绑定相关服务。

如有问题请参考 [Android 14 行为变更文档](https://developer.android.com/about/versions/14/behavior-changes-14)。

## 排查步骤

1. **检查 `AndroidManifest.xml` 权限声明**。确认是否已添加 `android.permission.FOREGROUND_SERVICE_MEDIA_PROJECTION` 权限。

2. **检查前台服务声明**。确认前台服务是否正确声明了 `foregroundServiceType="mediaProjection"`。

3. **检查代码执行顺序**。确认是否先获取屏幕权限，后绑定服务。

## 解决方法

1. 添加必要权限。
   ```XML
   <!-- AndroidManifest.xml 中添加 -->
   <uses-permission android:name="android.permission.FOREGROUND_SERVICE_MEDIA_PROJECTION" />
   ```

2. 更新服务声明。
   ```XML
   <!-- AndroidManifest.xml 中修改 -->
   <service
       android:name=".ScreenCaptureService"
       android:foregroundServiceType="mediaProjection" />
   ```

3. 修正代码执行顺序。必须先获取屏幕共享权限，再绑定屏幕录制服务。

   ```Java
   // 1. 首先获取用户的屏幕共享权限
   startActivityForResult(createScreenCaptureIntent(this), REQUEST_CODE_SCREEN_CAPTURE);

   // 2. 在权限回调中绑定服务
   @Override
   protected void onActivityResult(int requestCode, int resultCode, Intent data) {
       super.onActivityResult(requestCode, resultCode, data);
       if (requestCode == REQUEST_CODE_SCREEN_CAPTURE && resultCode == RESULT_OK) {
           // 仅在获得权限后绑定服务
           ScreenCaptureService.bindScreenService();
       }
   }
   ```