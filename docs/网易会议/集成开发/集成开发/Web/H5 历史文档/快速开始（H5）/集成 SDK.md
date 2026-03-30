本文介绍在 H5 页面集成网易会议组件 NEMeetingKit。

## 前提条件

在根据本文操作前，请确保您已在网易云信控制台上，完成以下设置：

1. 在 [网易云信控制台](https://app.yunxin.163.com/global/home) 创建至少一个应用。若无应用，请参考 <a href="https://doc.yunxin.163.com/console/concept/TIzMDE4NTA">创建应用并获取 AppKey</a>。
2. 开通 **视频会议** 解决方案。具体步骤可参考 [方案开通](https://doc.yunxin.163.com/meeting/concept/TkzMjExNDY?platform=client)。

## 开发环境

在客户端实现音视频会议功能之前，请您准备以下开发环境：

| 环境类型 | 具体要求 |
| ---- | ---- |
| 浏览器 | - 移动版 Chrome：74 及以上版本 |\
| | - 移动版 Safari：13 及以上版本 <note type="notice">iOS 13.0 ～ 14.3 的系统版本，仅支持播放远端音视频，本端的音视频流无法发送。</note> |
| Node | 8 及以上版本 |

## 注意事项

- 请使用 HTTPS 协议访问网易会议组件的 Domain。
- 不建议通过 require 方式引入 SDK，可能存在选择设备无效等问题。

## 方式 1：通过 script 标签引入 SDK

### 配置步骤

1. 在本地文件夹中创建网易会议组件的项目文件夹，并将解压后的网易会议组件 SDK 拷贝到项目文件夹中。文件目录类似如下：

    ```Bash
    ├── index.html
    ├── NEMeetingKit_V4.x.x.js
    ```
2. 将如下代码添加到 `index.html` 页面的 body 底部中。

    ```JavaScript
    <script src="./NEMeetingKit_V4.x.x.js"></script>//将文件路径替换为网易会议组件在本地的相对路径，版本号请替换为对应的版本号
    ```

3. 在页面添加 ID 为 `ne-web-meeting` 的元素（用于挂载网易会议组件）。

    ```HTML
    <div id="ne-web-meeting"></div>
    ```

    ::: note note
    该 ID 为固定值，请不要修改。
    :::

4. 初始化网易会议组件。

    ```JavaScript
    NEMeetingKit.actions.init(800, 800, config, (e) => {
        // 初始化完成回调
    });
    ```

### 示例代码

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
  <div id="ne-web-meeting"></div>
  <script src="./NEMeetingKit_1.0.0.umd.js"></script> //将文件路径替换为网易会议组件在本地的相对路径，版本号请替换为对应的版本号
  <script>
    /* 初始化
        * @param width：宽度(px)，为 0 则表示 100%
        * @param height：高度(px)，为 0 则表示 100%
        * @param config：入会配置
        * @param callback：回调
    */
    function init() {
        const config = {
            appKey: "", //网易云信服务 appkey
        };
        NEMeetingKit.actions.init(0, 0, config, () => {
            console.log('init 回调')

            // 检测浏览器兼容性
            NEMeetingKit.actions.checkSystemRequirements(
                function (err, result) {
                    let str = ''
                    if (err) {
                        str = err
                    } else {
                        str = result ? "支持" : "不支持"
                    }
                    console.log('浏览器兼容性检测结果：', str)
                }
            )

            // 事件监听
            NEMeetingKit.actions.on("peerJoin", (members) => {
                console.log("成员加入回调", members);
            });
            NEMeetingKit.actions.on("peerLeave", (uuids) => {
                console.log("成员离开回调", uuids);
            });
            NEMeetingKit.actions.on("roomEnded", (reason) => {
                console.log("房间被关闭", reason);
            });

        });

        // 获取会议相关信息
        const MeetingInfo = NEMeetingKit.actions.NEMeetingInfo // 会议基本信息
        const memberInfo = NEMeetingKit.actions.memberInfo // 当前成员信息
        const joinMemberInfo = NEMeetingKit.actions.joinMemberInfo // 入会成员信息
    }
    // token 登录
    NEMeetingKit.actions.login({
            accountId: accountId, // 账号
            accountToken: accountToken, // token
        },
        function (e) {
            console.log('login 回调', e)
        }
    );

    // 加入会议，需要先进行 token 登录
    NEMeetingKit.actions.join({
            meetingId: 'meetingId', // 会议号
            nickName: 'nickName', // 会中昵称
            video: 2, // 视频开关，1 为打开 2 为关闭
            audio: 2, // 音频开关，1 为打开 2 为关闭
        },
        function (e) {
            console.log('加入会议回调', e);
        }
    );

    // 登出
    NEMeetingKit.actions.logout(
        function (e) {
            console.log('logout 回调', e)
        }
    )

    // 取消监听
    NEMeetingKit.actions.off("peerJoin")
    NEMeetingKit.actions.off("peerLeave")
    NEMeetingKit.actions.off("roomEnded")

    // 销毁 sdk
    NEMeetingKit.actions.destroy(); // 销毁
  </script>
</body>
</html>
```

## 方式 2：通过 NPM 包集成

1. 在项目中安装依赖。

    ```NPM
    npm install nemeeting-web-sdk --save
    ```
2. 在对应的 js 文件中引入。

    ```JavaScript
    import NEMeetingKit from 'nemeeting-web-sdk'
    ```

## 下一步

调用网易会议组件接口 [实现基础功能](https://doc.yunxin.163.com/meeting/guide/TQ4MTU2NzQ?platform=web)，例如调用初始化接口，并传入您在网易云信控制台上创建应用时获取的密钥（AppKey）。