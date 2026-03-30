## 问题现象

升级到 Flutter UIKit [10.2.0](https://doc.yunxin.163.com/messaging-uikit/concept/jY4MjM0NDc?platform=client#1020-2025-05-26) 版本后出现运行时报错，典型错误信息如下：

<img alt="image-netease" src="https://yx-web-nosdn.netease.im/common/d1785a46ac993d8546e2ed30cd9d1dd2/image.png" style="width:80%;border: 1px solid #BFBFBF;">

## 问题原因

Flutter UIKit 在 10.2.0 版本进行了重大架构调整：

- **依赖变更**：去除了对 `netease_corekit_im` 的依赖。
- **代码整合**：将 `netease_corekit_im` 中的代码整合到了 `nim_chatkit` 中。
- **自动升级冲突**：如果项目中使用了版本向上兼容符号（`^`），会导致自动升级到 10.2.0 版本，引起兼容性问题。

## 排查步骤

1. 查看 `pubspec.yaml` 文件中的 UIKit 版本：
   ```yaml
   dependencies:
     nim_conversationkit_ui: ^10.x.x
     nim_chatkit_ui: ^10.x.x
     # 其他 kit...
   ```

2. 确认报错类型。

   - **编译时报错**：通常是 `import` 路径问题。
   - **运行时报错**：可能是版本不匹配导致的 API 调用异常。

3. 运行以下命令检查依赖关系。
   ```bash
   flutter pub deps
   ```

## 解决方案

根据项目需求，选择以下两种解决方案之一：

### 方案一：升级到 10.2.0（推荐）

1. 在 `pubspec.yaml` 中将所有相关 Kit 升级到 10.2.0：

    ```yaml
    dependencies:
    nim_conversationkit_ui: ^10.2.0
    nim_chatkit_ui: ^10.2.0
    nim_teamkit_ui: ^10.2.0
    nim_contactkit_ui: ^10.2.0
    nim_searchkit_ui: ^10.2.0
    # 移除以下依赖
    # netease_corekit_im: # 删除此行
    ```

2. 清理和重新获取依赖。

    ```bash
    flutter clean
    flutter pub get
    ```

3. 修复 `import` 报错。

    如果出现编译报错，需要更新 `import` 语句：

    ```Dart
    // 旧的 import（需要修改）
    import 'package:netease_corekit_im/xxx.dart';

    // 新的 import（修改后）
    import 'package:nim_chatkit/xxx.dart';
    ```

4. 重新编译测试。

    ```bash
    flutter run
    ```

### 方案二：保持当前版本

如果您暂时不想升级，可以锁定版本号：

1. 锁定版本号。

    在 `pubspec.yaml` 中移除 `^` 符号，指定具体版本：

    ```yaml
    dependencies:
    nim_conversationkit_ui: 10.1.0
    nim_chatkit_ui: 10.1.0
    nim_teamkit_ui: 10.1.0
    nim_contactkit_ui: 10.1.0
    nim_searchkit_ui: 10.1.0
    nim_chatkit: 10.1.0
    ```

2. 清理和重新获取依赖。

    ```bash
    flutter clean
    flutter pub get
    ```

3. 重新编译测试。

    ```bash
    flutter run
    ```

## 注意事项

- **版本一致性**：确保所有相关 Kit 使用相同版本号
- **彻底清理**：升级前务必执行 `flutter clean` 清理缓存
- **备份代码**：升级前建议备份当前工作代码
- **测试验证**：升级后需要充分测试相关功能