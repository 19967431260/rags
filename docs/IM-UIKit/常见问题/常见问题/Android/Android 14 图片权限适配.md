如果您项目中的 `SdkVersion` 采用 Android 14（34） ，那么您需要修改其中的权限申请，才能正常使用 IM UIKit 的图片发送功能。

## 媒体权限变更

Android 14 图片访问权限进行了调整，新增加 `READ_MEDIA_VISUAL_USER_SELECTED` 权限控制，您需要进行适配，否则无法在用户同意选择部分权限下查看并发送图片消息。

如下图所示：

![Android14.png](https://yx-web-nosdn.netease.im/common/6b4be41afcf978100c5941a300045126/Android14.png)

详情请参考 《安卓官方文档》 的 [行为变更](https://developer.android.com/about/versions/14/behavior-changes-14?hl=zh-cn)。

## 修改权限申请

本文基于 IMUIKit 9.7.0 版本代码为例进行说明，其他 9.* 的版本按照改动移植到代码即可。

### 系统配置

1. 在 AndroidManifest 中增加权限声明。

```java
<!-- android 33 image--><uses-permission android:name="android.permission.READ_MEDIA_IMAGES"/>
<uses-permission android:name="android.permission.READ_MEDIA_VIDEO"/>
<!-- android 34 image--><uses-permission android:name="android.permission.READ_MEDIA_VISUAL_USER_SELECTED"/>
```

2. 升级依赖库。

```java
implementation("androidx.appcompat:appcompat:1.6.1")
implementation("com.google.android.material:material:1.11.0")
```

### ChatBaseFragment

1、修改图片库 `Launcher pickMediaLauncher`。将声明类型替换为 `ActivityResultLauncher<PickVisualMediaRequest>`。

```java
protected ActivityResultLauncher<PickVisualMediaRequest> pickMediaLauncher;

// 系统图片&视频选择器，选择结果处理
pickMediaLauncher = registerForActivityResult(
                new ActivityResultContracts.PickVisualMedia(),
                uri -> {
                  // Callback is invoked after the user selects a media item or closes the                  // photo picker.                  if (uri != null) {
                    ALog.d(LIB_TAG, LOG_TAG, "pick media result uri -->> " + uri);
                    mHandler.postDelayed(
                            () -> viewModel.sendImageOrVideoMessage(uri),
                            100);
                  } else {
                    ALog.d(LIB_TAG, LOG_TAG, "PhotoPicker No media selected");
                  }
                });
```

2. 修改图片库启动代码，将 `startPickMedia` 方法替换为新的实现逻辑。

```java
protected void startPickMedia() {
  pickMediaLauncher.launch(
          new PickVisualMediaRequest.Builder()
                  .setMediaType(ActivityResultContracts.PickVisualMedia.ImageAndVideo.INSTANCE)
                  .build());
}
```

3. 在 `pickMedia` 方法中新增对版本权限的判断逻辑。

```java
public void pickMedia() {

  String[] permission = new String[] {Manifest.permission.READ_EXTERNAL_STORAGE};

  if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.UPSIDE_DOWN_CAKE) {
    permission =
            new String[] {
                    Manifest.permission.READ_MEDIA_IMAGES,
                    Manifest.permission.READ_MEDIA_VIDEO,
                    Manifest.permission.READ_MEDIA_VISUAL_USER_SELECTED            };
    // 根据系统版本判断，如果是Android13则采用Manifest.permission.READ_MEDIA_IMAGES  } else if (Build.VERSION.SDK_INT == Build.VERSION_CODES.TIRAMISU) {
    permission =
            new String[] {
                    Manifest.permission.READ_MEDIA_IMAGES, Manifest.permission.READ_MEDIA_VIDEO            };
  }
  if (PermissionUtils.hasPermissions(ChatBaseFragment.this.getContext(), permission)) {
    startPickMedia();
  } else {
    requestCameraPermission(
            permission,
            REQUEST_READ_EXTERNAL_STORAGE_PERMISSION_ALBUM);
  }
}
```

### ChatBaseViewmodel

修改发送图片消息方法 `sendImageOrVideoMessage`。

```java
public void sendImageOrVideoMessage(Uri uri) {
    ALog.d(LIB_TAG, TAG, "sendImageOrVideoMessage:" + uri);
    if (uri == null) {
        return;
    }
    String mimeType = "";
    try {
        String realPath = UriUtils.uri2FileRealPath(uri);
        mimeType = FileUtils.getFileExtension(realPath);
    } catch (IllegalStateException e) {
        ToastX.showShortToast(R.string.chat_message_type_resource_error);
        return;
    }
    if (ImageUtil.isValidPictureFile(mimeType)) {
        SendMediaHelper.handleImage(uri, true, this::sendImageMessage);
    } else if (ImageUtil.isValidVideoFile(mimeType)) {
        SendMediaHelper.handleVideo(
                uri,
                file -> {
                    MediaMetadataRetriever mmr = new MediaMetadataRetriever();
                    try {
                        mmr.setDataSource(file.getPath());
                        String duration = mmr.extractMetadata(MediaMetadataRetriever.METADATA_KEY_DURATION);
                        String width = mmr.extractMetadata(MediaMetadataRetriever.METADATA_KEY_VIDEO_WIDTH);
                        String height = mmr.extractMetadata(MediaMetadataRetriever.METADATA_KEY_VIDEO_HEIGHT);
                        String orientation =
                                mmr.extractMetadata(MediaMetadataRetriever.METADATA_KEY_VIDEO_ROTATION);
                        if (TextUtils.equals(orientation, Orientation_Vertical)) {
                            String local = width;
                            width = height;
                            height = local;
                        }
                        ALog.d(
                                LIB_TAG,
                                TAG,
                                "width:" + width + "height" + height + "orientation:" + orientation);
                        sendVideoMessage(
                                file,
                                Long.parseLong(duration),
                                Integer.parseInt(width),
                                Integer.parseInt(height),
                                file.getName());
                    } catch (Exception e) {
                        e.printStackTrace();
                    } finally {
                        try {
                            mmr.release();
                        } catch (IOException e) {
                            e.printStackTrace();
                        }
                    }
                });
    } else {
        ToastX.showShortToast(R.string.chat_message_type_not_support_tips);
        ALog.d(LIB_TAG, TAG, "invalid file type");
    }
}
```

变更如下图所示：

![变更对比.png](https://yx-web-nosdn.netease.im/common/90618b8bb83262a4878bc52bf827699a/变更对比.png)