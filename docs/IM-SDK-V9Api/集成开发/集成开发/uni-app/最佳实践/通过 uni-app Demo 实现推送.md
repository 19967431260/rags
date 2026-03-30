
为了提高消息送达率，云信引入手机系统厂商推送。目前支持的厂商包括小米、华为、vivo、OPPO、魅族、谷歌 FCM。暂不支持荣耀推送。

若您引入 IM uni-app SDK，可直接参考[uni-app 离线推送](https://doc.yunxin.163.com/messaging/guide/DQ1NTAxNzI?platform=uniapp) 文档实现。

若您想通过 <b>uni-app Demo（UIKit）</b>实现推送，那么请参考本文示例实现。


## 实现步骤

uni-app 的推送需要以下步骤，其中，除第三步**实现离线推送**外，其他步骤都可参考 [uni-app 离线推送](https://doc.yunxin.163.com/messaging/guide/DQ1NTAxNzI?platform=uniapp)。

一、上传推送证书至云信控制台
二、设置 uni-app 工程
三、实现离线推送
四、测试离线推送

本节主要介绍第三步**实现离线推送**。

1. 安装并引入 @xkit-yx/core-kit。

    ```
    import { NimKitCore } from '@xkit-yx/core-kit/dist/uniapp-nim-core'
    ```

2. 初始化时设置各厂商的推送证书等推送配置。

    :::note notice
    代码中各个厂商的证书，如 `xmCertificateName`、`hwCertificateName` 等需要和云信控制台中配置的证书名称保持一致。
    :::

    ```
    <script  lang="ts">
    import RootStore, { type IMMessage } from '@xkit-yx/im-store'
    import { NimKitCore } from '@xkit-yx/core-kit/dist/uniapp-nim-core'
    import { getMsgContentTipByType } from './utils/msg'
    import { getUniPlatform } from './utils'

    // #ifdef APP-PLUS
    const nimPushPlugin = uni.requireNativePlugin('NIMUniPlugin-PluginModule')
    // #endif

    export default {
    onLaunch() {
        this.initNim(imOptions)
    },
    methods: {
        initNim(opts: { account: string, token: string }) {
        const isWeixinApp = getUniPlatform() === 'mp-weixin'
        // @ts-ignore
        const nim = uni.$UIKitNIM = new NimKitCore({
            initOptions: {
            "appkey": "", // 请填写你的appkey
                "account": "", // 请填写你的account
                "token": "", // 请填写你的token
            "lbsUrls": isWeixinApp ? [
                "https://lbs.netease.im/lbs/wxwebconf.jsp"
            ]:[
                "https://lbs.netease.im/lbs/webconf.jsp"
            ],
            "linkUrl": "weblink.netease.im",
            "needReconnect": true,
            /**
            * 使用固定设备ID，
            */
            isFixedDeviceId: true,
            // "reconnectionAttempts": 5,
            debugLevel: 'debug',
            ...opts,
            },
            platform: 'UniApp',
        })

        // @ts-ignore
        const store = uni.$UIKitStore = new RootStore(nim, {
            addFriendNeedVerify: false,
            teamBeInviteMode: 'noVerify',
            teamJoinMode: 'noVerify',
            teamUpdateExtMode: 'all',
            teamUpdateTeamMode: 'all',
            teamInviteMode: 'all',
            sendMsgBefore: async (options: any, type: IMMessage['type']) => {
            const pushContent = getMsgContentTipByType({ body: options.body, type })
            const yxAitMsg = options.ext ? options.ext.yxAitMsg : { forcePushIDsList: '[]', needForcePush: false }

            // 如果是 at 消息，需要走离线强推
            const { forcePushIDsList, needForcePush } = yxAitMsg
                // @ts-ignore
                ? store.msgStore._formatExtAitToPushInfo(yxAitMsg, options.body)
                : { forcePushIDsList: '[]', needForcePush: false }

            console.log('forcePushIDsList: ', forcePushIDsList)

            // 不同产商的推送消息体
            const { scene, to } = options
            const pushPayload = JSON.stringify({
                // oppo
                oppoField: {
                "click_action_type": 4, // 参考 oppo 官网
                "click_action_activity": '', // 各端不一样 TODO
                "action_parameters": { "sessionId": scene, "sessionType": to } // 自定义
                },

                // vivo
                vivoField: {
                "pushMode": 0 //推送模式 0：正式推送；1：测试推送，不填默认为0
                },

                // huawei
                hwField: {
                click_action: {
                    'type': 1,
                    'action': '' // 各端不一样 TODO
                },
                androidConfig: {
                    'category': 'IM',
                    'data': JSON.stringify({ 'sessionId': to, 'sessionType': scene })
                }
                },

                // 通用
                sessionId: to,
                sessionType: scene
            })

            const pushInfo = {
                needPush: true,
                needPushBadge: true,
                pushPayload: '{}',
                pushContent,
                needForcePush,
                forcePushIDsList,
                forcePushContent: pushContent,
            }
            return { ...options, pushInfo }
            },
        })

        // #ifdef APP-PLUS
        // 注册推送
        nim.getNIM().offlinePush.setOfflinePushConfig({
            plugin: nimPushPlugin,
            authConfig: {
            // xiaomi
            xmAppId: "1111",
            xmAppKey: "1111",
            xmCertificateName: "KIT_UNIAPP_MI_PUSH",

            // huawei
            hwAppId: "1111",
            hwCertificateName: "KIT_UNIAPP_HW_PUSH",

            // oppo
            oppoAppId: "1111",
            oppoAppKey: "1111",
            oppoAppSecret: "1111",
            oppoCertificateName: "KIT_UNIAPP_OPPO_PUSH",

            /**
            * 注意vivo的appid和appkey需要同时在此处，以及manifest.json(即插件参数配置)中配置
            */
            vivoAppId: "1111",
            vivoAppKey: "1111",
            vivoCertificateName: "KIT_UNIAPP_VIVO_PUSH",

            // fcm
            fcmCertificateName: "KIT_UNIAPP_FCM_PUSH",

            // meizu
            mzAppId: "1111",
            mzAppKey: "1111",
            mzCertificateName: "KIT_UNIAPP_MZ_PUSH",

            // iOS
            apnsCertificateName: "dis_im_uniapp"
            }
        })
        // #endif

        nim.connect()
        },
        logout() {
        
        }
    }
    }

    </script>
    ```

3. 在 App.vue 中，监听应用是否退至后台，并通过 updateAppBackground 告知云信服务器应用状态。

    当应用退至后台时，Android 应用仍可以收到 IM SDK 的消息，开发者可以根据这些设置应用通知。而 iOS 则无法激活SDK的回调函数。因此，iOS 退至后台时，应该通过下面代码告知云信服务器，然后云信服务器会给处于后台的 iOS 应用发送离线推送。

    ```
    onShow() {
        // #ifdef APP-PLUS
        // @ts-ignore
        const nimSdk = uni?.$UIKitNIM?.getNIM()
        nimSdk?.offlinePush?.updateAppBackground({
        isBackground: false
        })
        // #endif
    }, 
    onHide() {
        // #ifdef APP-PLUS 
        // @ts-ignore
        const nimSdk = uni?.$UIKitNIM?.getNIM()
        nimSdk?.offlinePush?.updateAppBackground({
        isBackground: true
        })
        // #endif
    },
    ```
