登录对于 IM 产品来说至关重要，是后续业务顺利进行的前提条件。开发者集成 NIM SDK 的各项能力时，如果未能正确使用登录接口或处理登录状态，将引发不必要的问题，影响开发进度。本文仅介绍如何以最佳姿势进行**手动登录**和**自动登录**，进而实现 IM 登录。


- 手动登录：首次登录 IM 时调用`AuthService.login`方法实现。
- 自动登录（Windows 和 macOS 暂不支持）：手动登录 IM 成功之后调用，具体调用方式为在初始化时传入的上次登录的信息`NIMLoginInfo`。


::: note note
更多登录相关说明请参见[登录管理](https://doc.yunxin.163.com/messaging/docs/zk5NTg0NTg?platform=flutter)。
:::



## 前提条件

- 已[集成 NIM SDK](https://doc.yunxin.163.com/messaging/docs/Dg5NjI4MDg?platform=flutter)。
- 已通过云信服务端[注册 IM 账号](https://doc.yunxin.163.com/messaging/docs/DQ3Nzk1MTY?platform=server) ，获取 IM 账号（`accid`）和对应的`token`。

    您也可通过控制台注册 IM 测试账号。测试账号及对应的`token`仅适用于调试环境，线上生产环境必须将测试账号及其`token`替换为云信服务端生成的正式`accid`和`token`。

## 实现方案


### **手动登录**


IM 手动登录接口的调用，需要在用户登录应用时（即在应用的登录界面点击登录按钮时）进行，其他情况一般不需要调用手动登录接口。在登录界面中，IM 登录可以作为整个应用登录过程的一个环节。常见的方案是先实现应用自身账号体系的登录，成功后再使用返回的`accid`和`token`进行 IM 的登录。

- **手动登录流程**

    <br>

    ![手动登录流程图.png](https://yx-web-nosdn.netease.im/common/5dfd8fc1ecda5fde88b261129b4c316a/手动登录流程图.png)



  
- **接口调用**

    1. 调用[`AuthService.login`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AuthService/login.html)方法手动登录云信IM。
    2. 调用后处理。
        - 如果登录成功，保存 IM 的`accid`和`token`到本地，方便下次应用启动自动登录时使用。
        - 如果登录失败，清理本地保存的用户登录信息，防止下次启动走自动登录逻辑。

    示例代码如下：




    ```
        NimCore.instance.authService.login(NIMLoginInfo(
      account: account,
      token: token,
    )).then((result){
      if(result.isSuccess){
      //todo 保存accid、token，用于下次自动登录。
      }else{
        //todo 清理登录账号、token缓存，调用login失败后，不允许走自动登录。
      }
    });
    ```



### **自动登录**

手动登录 IM 成功后，下次启动应用可以使用云信 IM 的自动登录模式。自动登录后，即使登录未完成或者网络无法访问，应用也可以直接访问用户本地 SDK 数据。


- **自动登录流程**

    <br>



    <img style="width:80%" src="https://yx-web-nosdn.netease.im/common/917f8f5febf61b527be700eb8afc73b3/自动登录流程图.png" />


- **接口调用**

    初始化 NIM SDK 时（如调用[`NimCore.initialize`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NimCore/initialize.html)方法），传入上次登录的[`autoLoginInfo`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/NIMSDKOptions/autoLoginInfo.html)对象，即可实现自动登录。

    自动登录的**使用限制**如下：

    - 自动登录只能登录上次登录的IM 账号，不能登录其他账号。
    - 需要某个 IM 账号曾经通过手动登录接口登录成功后才可以调用。
    - 无论之前是否曾经手动登录成功，只要最近一次手动登录接口调用失败，则不可以继续自动登录。
    - 当收到`KICKOUT`、`KICK_BY_OTHER_CLIENT`、`FORBIDDEN`、`PWD_ERROR`、`DATA_UPGRADE`这些[IM 登录状态](https://doc.yunxin.163.com/messaging/docs/TI1MTU1NDc?platform=android#登录状态说明)时，后续自动登录将无效，需要用户通过手动登录接口重新登录。更多相关说明，见下文的[登录状态处理](#登录状态处理)。




    实现自动登录的示例代码如下：



    ```
    //todo 获取之前登录成功保存的accid、token信息。之前已经登录过，可以走自动登录。
    var account = '';
    var token = '';
    late NIMSDKOptions options;
    if (Platform.isAndroid) {
      final directory = await getExternalStorageDirectory();
      options = NIMAndroidSDKOptions(
          appKey: appKey,
          shouldSyncStickTopSessionInfos: true,
          autoLoginInfo: NIMLoginInfo(account: account,token: token),
          sdkRootDir:
          directory != null ? '${directory.path}/NIMFlutter' : null);
    } else  {
      final directory = await getApplicationDocumentsDirectory();
      options = NIMIOSSDKOptions(
        appKey: appKey,
        shouldSyncStickTopSessionInfos: true,
        sdkRootDir: '${directory.path}/NIMFlutter',
        autoLoginInfo: NIMLoginInfo(account: account,token: token),
      );
    }

    NimCore.instance.initialize(options).then((value){
      if(value.isSuccess){
        //todo 初始化成功
      }else{
        //todo 初始化失败
      }
    });
    ```

### **登录状态处理**


[IM 登录状态](https://doc.yunxin.163.com/messaging/docs/zk5NTg0NTg?platform=flutter#监听登录状态变化)表示当前登录的 NIM SDK 实例与云信服务端的长连接状态，也可以理解为用户设备和云信服务端的网络连接状态。调用初始化接口之后，可以在应用的主界面注册[`authStatus`](https://doc.yunxin.163.com/messaging/references/flutter/dartdoc/Latest/zh/nim_core/AuthService/authStatus.html)方法注册 IM 的登录状态事件流，监听当前的登录状态，并通过 UI 层提示用户。其他使用场景一般只需要在手动登录成功后或者自动登录期间才需要处理 IM 登录状态。

::: note notice
`authStatus`事件流必须在 NIM SDK 初始化之后注册。
:::


<br>

登录状态处理的流程图如下：


<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/2a7ae5f4dcffef678966cc8ad5fcf5ad/登录状态处理流程.png" />



示例代码如下：

```
 NimCore.instance.authService.authStatus.listen((event) {
      //TODO 1.如果尚未登录过，可以根据自己业务需求确定是否需要进入登录页面
      //TODO 2.如果登录过，并且不能自动重连的情况下，必须跳转到登录页面
      switch(event.status){
        case NIMAuthStatus.unLogin:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.connecting:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.logging:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.loggedIn:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.forbidden:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.netBroken:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.versionError:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.pwdError:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.kickOut:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.kickOutByOtherClient:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.dataSyncStart:
          // TODO: Handle this case.
          break;
        case NIMAuthStatus.dataSyncFinish:
          // TODO: Handle this case.
          break;
        default:
          break;
      }
    });
```

  





