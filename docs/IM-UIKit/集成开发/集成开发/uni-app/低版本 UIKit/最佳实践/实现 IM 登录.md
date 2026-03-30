本文主要介绍如何结合业务侧登录和 IM 登录。

## 概述

用户业务侧的登录需要结合云信 IM 的登录实现。

在您的登录页完成登录后，调用 app.vue 中注册的登录方法，将您的业务服务器返回的 `account`、`token` 传入 app.vue 里的初始化登录 IM 的方法，待 IM 初始化、连接完成后，再重定向到您需要的界面。

## 实现

1. 在 app.vue 中注册登录方法，在 onLaunch 里判断是否已经登录，如果未登录，重定向到登录页面。

    ```
    <script lang="ts">
    import RootStore, { type IMMessage } from '@xkit-yx/im-store'
    // @ts-ignore
    import { NimKitCore } from '@xkit-yx/core-kit/dist/uniapp-nim-core'
    import {
    customRedirectTo,
    customReLaunch,
    customSwitchTab,
    } from './utils/customNavigate'
    import { getMsgContentTipByType } from './utils/msg'
    import { STORAGE_KEY } from './utils/constants'
    import { isWxApp } from './utils'

    export default {
    onLaunch() {
        // 如果IM已经完成连接，说明此时一定已经登录，直接return即可
        if (
        // @ts-ignore
        uni.$UIKitStore &&
        // @ts-ignore
        uni.$UIKitStore?.connectStore?.connectState === 'connected'
        ) {
        return
        }
        const imOptions = uni.getStorageSync(STORAGE_KEY)
        // 在此处判断是否已经登陆
        if (imOptions) {
        this.initNim(imOptions)
        } else {
        // 需要登录 im
        customRedirectTo({
            url: '/pages/Login/index',
        })
        }
    },
    // 在app.vue 的methods注册 initNim
    methods: {
        initNim(opts: { account: string; token: string }) {
        // 保存登录信息
        // @ts-ignore
        uni.setStorage({
            key: STORAGE_KEY,
            data: opts,
            success: function () {
            console.log('保存登录信息success')
            },
        })
        // @ts-ignore
        const nim = (uni.$UIKitNIM = new NimKitCore({
            initOptions: {
            appkey: '',
            lbsUrls: isWxApp
                ? ['https://lbs.netease.im/lbs/wxwebconf.jsp']
                : ['https://lbs.netease.im/lbs/webconf.jsp'],
            linkUrl: isWxApp ? 'wlnimsc0.netease.im' : 'weblink.netease.im',
            needReconnect: true,
            /**
            * 使用固定设备ID，
            */
            isFixedDeviceId: true,
            // "reconnectionAttempts": 5,
            debugLevel: 'debug',
            ...opts,
            },
            platform: 'UniApp',
        }))

        // @ts-ignore
        const store = (uni.$UIKitStore = new RootStore(nim, {
            addFriendNeedVerify: false,
            teamBeInviteMode: 'noVerify',
            teamJoinMode: 'noVerify',
            teamUpdateExtMode: 'manager',
            teamUpdateTeamMode: 'manager',
            teamInviteMode: 'manager',
            sendMsgBefore: async (options: any, type: IMMessage['type']) => {
            const pushContent = getMsgContentTipByType({
                body: options.body,
                type,
            })
            const yxAitMsg = options.ext
                ? options.ext.yxAitMsg
                : { forcePushIDsList: '[]', needForcePush: false }

            // 如果是 at 消息，需要走离线强推
            // @ts-ignore
            const { forcePushIDsList, needForcePush } = yxAitMsg
                ? // @ts-ignore
                store.msgStore._formatExtAitToPushInfo(yxAitMsg, options.body)
                : { forcePushIDsList: '[]', needForcePush: false }

            console.log('forcePushIDsList: ', forcePushIDsList)

            // 不同产商的推送消息体
            const { scene, to } = options
            const pushPayload = JSON.stringify({
                // oppo
                oppoField: {
                click_action_type: 4, // 参考 oppo 官网
                click_action_activity: '', // 各端不一样 TODO
                action_parameters: { sessionId: scene, sessionType: to }, // 自定义
                },

                // vivo
                vivoField: {
                pushMode: 0, //推送模式 0：正式推送；1：测试推送，不填默认为0
                },

                // huawei
                hwField: {
                click_action: {
                    type: 1,
                    action: '', // 各端不一样 TODO
                },
                androidConfig: {
                    category: 'IM',
                    data: JSON.stringify({ sessionId: to, sessionType: scene }),
                },
                },

                // 通用
                sessionId: to,
                sessionType: scene,
            })

            const pushInfo: any = {
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
        }))
        nim.connect()
        // 登录完成，定向到您需要的页面
        customSwitchTab({
            url: '/pages/Conversation/index',
        })
        },
        logout() {
        // @ts-ignore
        uni.removeStorageSync(STORAGE_KEY)
        // @ts-ignore
        uni.$UIKitNIM.disconnect()
        // @ts-ignore
        uni.$UIKitStore.destroy()
        customReLaunch({
            url: '/pages/Login/index',
        })
        },
    },
    }
    </script>
    ```

2. 在登录页完成您的业务服务器登录后，调用 app.vue 中注册的 IM 登录方法，并传入业务服务器返回的`accid`、`token`。

    ```
    //  pages/Login/index.vue

    async function submitLoginForm() {
    try {
        // loginRegisterByCode 您需要结合您的业务需求自行实现
        const res = await loginRegisterByCode(loginForm)
        const app = getApp()
        // 调用app.vue 中的注册的im登录方法
        app.initNim({ account: res.imAccid, token: res.imToken })
    } catch (error: any) {
        uni.showToast({
        title: msg,
        icon: 'none'
        })
    }
    }
    ```