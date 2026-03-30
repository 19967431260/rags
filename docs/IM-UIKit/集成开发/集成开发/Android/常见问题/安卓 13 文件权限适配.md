如果您项目中的 `SdkVersion` 采用 Android 13（33）版本，那么您需要修改其中的权限申请，才能正常使用 NIM UIKit 的图片和文件发送功能。

## 媒体权限变更

Android 13 权限变化请访问《安卓官方文档》[行为变更：以 Android 13 或更高版本为目标平台的应用](https://developer.android.com/about/versions/13/behavior-changes-13?hl=zh-cn#granular-media-permissions) 查看细化的媒体权限。

<!-- 如下图所示：

<img alt="Android13 权限变化.png" src="https://yx-web-nosdn.netease.im/common/623f8d0c0f67a6f53101c789d56aa257/Android13权限变化.png" style="width:80%;border: 1px solid #BFBFBF;"> -->

## 文件权限定位

NIM UIKit 文件权限的相关逻辑代码位于 `chatkit-ui` 模块中，代码实现在 `chatBaseFragment`。

## 修改权限申请

### 发送图片或文件前

声明常量变量：`REQUEST_READ_MEDIA_PERMISSION`。

```Java
private static final int REQUEST_PERMISSION = 0;
private static final int REQUEST_CAMERA_PERMISSION = 1;
private static final int REQUEST_VIDEO_PERMISSION = 2;
private static final int REQUEST_READ_EXTERNAL_STORAGE_PERMISSION = 3;
private static final int REQUEST_READ_MEDIA_PERMISSION = 4;
```

主要修改 `pickMedia` 和 `sendFile` 方法，在进行发送之前需要根据系统版本申请不同的权限。

```Java
private final IMessageProxy messageProxy =
    new IMessageProxy() {
      @Override
      public boolean sendTextMessage(String msg, ChatMessageBean replyMsg) {
        ....
      }

      @Override
      public void pickMedia() {
        String permission = Manifest.permission.READ_EXTERNAL_STORAGE;
        //根据系统版本判断，如果是 Android13 则采用 Manifest.permission.READ_MEDIA_IMAGES
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {
          permission = Manifest.permission.READ_MEDIA_IMAGES;
        }
        if (PermissionUtils.hasPermissions(
            ChatBaseFragment.this.getContext(), permission)) {
          startPickMedia();
        } else {
          requestCameraPermission(
                  permission,
              REQUEST_READ_MEDIA_PERMISSION);
        }
      }

      @Override
      public void takePicture() {
       .....
      }

      @Override
      public void captureVideo() {
        .....
      }

      @Override
      public boolean sendFile() {
        String permission = Manifest.permission.READ_EXTERNAL_STORAGE;
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU) {
            //根据系统版本判断，如果是 Android13 则采用 Manifest.permission.READ_MEDIA_IMAGES
          permission = Manifest.permission.READ_MEDIA_VIDEO;
        }
        if (PermissionUtils.hasPermissions(
                ChatBaseFragment.this.getContext(), permission)) {
          startPickFile();
        } else {
          requestCameraPermission(
                  permission,
                  REQUEST_READ_EXTERNAL_STORAGE_PERMISSION);
        }
        return true;
      }
      ....
   }
```

### 唤起文件选择器

在系统弹窗申请权限之后，通过判断用户操作的结果，来拉取文件选择器。

```Java
permissionLauncher =
    registerForActivityResult(
        new ActivityResultContracts.RequestMultiplePermissions(),
        result -> {
          if (result != null) {
            for (Map.Entry<String, Boolean> entry : result.entrySet()) {
              String permission = entry.getKey().toString();
              boolean grant = (Boolean) entry.getValue();
              if (grant) {
                if (TextUtils.equals(permission, Manifest.permission.CAMERA)) {
                  if (currentRequest == REQUEST_CAMERA_PERMISSION) {
                    startTakePicture();
                  } else if (currentRequest == REQUEST_VIDEO_PERMISSION) {
                    startCaptureVideo();
                  }
                }
                //====================
                //主要改动，在这里判断申请权限的类型中，增加 Android13 新增的多媒体权限
                else if (TextUtils.equals(
                    permission, Manifest.permission.READ_MEDIA_IMAGES) || TextUtils.equals(
                        permission, Manifest.permission.READ_MEDIA_VIDEO) || TextUtils.equals(
                        permission, Manifest.permission.READ_EXTERNAL_STORAGE)) {
                  if (currentRequest == REQUEST_READ_EXTERNAL_STORAGE_PERMISSION){
                    startPickFile();
                  }else {
                    startPickMedia();
                  }
                }
                //=====================
              } else {
                if (shouldShowRequestPermissionRationale(permission)) {
                  if (chatConfig == null
                      || chatConfig.permissionListener == null
                      || !chatConfig.permissionListener.requestPermissionDenied(
                          ChatBaseFragment.this.getActivity(), permission)) {
                    ToastX.showShortToast(
                        getResources().getString(R.string.permission_deny_tips));
                  }
                } else {
                  if (chatConfig == null
                      || chatConfig.permissionListener == null
                      || !chatConfig.permissionListener.permissionDeniedForever(
                          ChatBaseFragment.this.getActivity(), permission)) {
                    ToastX.showShortToast(getPermissionText(permission));
                  }
                }
              }
            }
          }
        });
```