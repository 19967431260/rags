NetEase CallKit UI 提供了两种自定义方案，满足不同层次的定制需求。

## 基于源码自定义

如果您只需要对现有 UI 进行微调，可以通过直接修改云信提供的 UI 源代码。

1. 访问 [NECallKit Flutter 源码](https://github.com/netease-kit/NECallKit/tree/main/Flutter)。

2. 下载该目录下的所有文件（除了 `example` 文件夹）。

    <img alt="image-netease" src="https://yx-web-nosdn.netease.im/common/0c35ca56da9dcfe262549c39fdd5bbbd/Flutter%20%E5%91%BC%E5%8F%AB%E7%BB%84%E4%BB%B6%E6%BA%90%E7%A0%81%E7%9B%AE%E5%BD%95%E6%96%B0.png" style="width:50%;border: 1px solid #BFBFBF;">

3. 将下载的文件移动到您的项目目录中。

4. 在项目的 `pubspec.yaml` 文件中，添加以下依赖：

    ```yaml
    dependencies:
    netease_callkit_ui:
        path: ./netease_callkit_ui  # 指向下载的源码目录
    netease_callkit: ^latest_version
    nim_core_v2: ^latest_version
    ```

5. 运行 `flutter pub get` 获取依赖。

6. 自定义 UI。

    - 替换图标和资源：直接替换 `assets/images` 文件夹下的图标，确保文件名不变即可。

    - 替换铃声：替换 `assets/audios` 文件夹下的音频文件：

        - `avchat_connecting.mp3` - 通话连接中音效
        - `avchat_ring.mp3` - 通话铃声

    - 国际化文案：修改 `lib/l10n` 目录下的国际化文件：

        - `intl_zh.arb` - 中文文案
        - `intl_en.arb` - 英文文案

## 完全自定义

如果您需要完全自定义 UI，可以集成 [无 UI 组件](https://doc.yunxin.163.com/nertccallkit/guide/DIxNDQ1MzE?platform=flutter)，然后基于 `NECallEngine` 实现自己的 UI 界面。