如果会话列表（`conversation-kit`）模块提供的默认界面无法满足您的业务需求，您可通过会话列表组件的自定义参数，自定义界面。

## 自定义参数

会话列表组件（`conversation-kit`）提供的自定义参数如下：

<div style="width:180px">参数</div> | 类型 | 说明
---- | ---- | ---- | ----
`renderSessionListEmpty` | `(() => Element)` | 自定义渲染会话列表为空时的内容，具体示例参考 [自定义 **会话列表为空时的内容**](#自定义会话列表为空时的内容)。
`renderCustomP2pSession` | `(options: {session: NimKitCoreTypes.ISession} & ConversationCallbackProps) => JSX.Element | null | undefined` | 自定义渲染会话类型是单聊的内容，具体示例参考 [自定义会话的展示内容](#自定义会话的展示内容)。
`renderCustomTeamSession` | `(options: {session: NimKitCoreTypes.ISession} & Omit<ConversationCallbackProps, 'onSessionItemMuteChange'>) => JSX.Element | null | undefined` | 自定义渲染会话类型是群聊的内容，具体示例参考 [自定义会话的展示内容](#自定义会话的展示内容)。
`renderSessionName` | `((options: { session: ISession; }) => Element | null)` | 自定义渲染会话名称。如果单聊会话定义了 renderCustomP2pSession 或群组会话定义了 renderCustomTeamSession 则不生效。具体示例参考 [自定义会话元素](#自定义会话元素)。
`renderSessionMsg` | `((options: { session: ISession; }) => Element | null)` | 自定义渲染会话消息。如果单聊会话定义了 renderCustomP2pSession 或群组会话定义了 renderCustomTeamSession 则不生效。
`renderP2pSessionAvatar` | `((options: { session: ISession; }) => Element | null)` | 自定义渲染 **单聊会话头像**。如果定义了 renderCustomP2pSession 则不生效。
`renderTeamSessionAvatar` | `((options: { session: ISession; }) => Element | null)` | 自定义渲染 **群聊会话头像**。如果定义了 renderCustomTeamSession 则不生效。
`prefix` | string | 样式前缀，默认值为"conversation"。
`commonPrefix` | string | 公共样式前缀，默认值为 "common"。
`onSessionItemClick` | `((id: string) => void)` | 会话单击事件。 |
`onSessionItemDeleteClick` | `((id: string) => void)` | 会话删除事件。 |
`onSessionItemStickTopChange` | `((id: string, isTop: boolean) => void)` | 会话置顶状态改变事件。 |
`onSessionItemMuteChange` | `((id: string, mute: boolean) => void)` | 会话免打扰状态改变事件。 |

## 自定义示例

<a id="自定义会话列表为空时的内容"></a>

### **会话列表为空的界面**

- [查看在线示例](https://codesandbox.io/p/sandbox/zi-ding-yi-hui-hua-lie-biao-wei-kong-shi-de-nei-rong-ys29dp)

    在 `IMAppProps` 传入正确的 `appkey`、`account` 和 `token` 即可在线预览效果。

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    const renderSessionListEmpty = () => {
      return (
        <div>
          <img style={{width: '100%'}} src='https://yx-web-nosdn.netease.im/common/2946c48f29d747305e68b1ddf27f3472/无成员可添加@3x.png'/>
          <div className='no-session'>暂无会话</div>
        </div>
      )
    }

    <ConversationContainer renderSessionListEmpty={renderSessionListEmpty}></ConversationContainer>
    ```
    :::
    ::: code Vue2/Vue3
    ```JavaScript/TypeScript
    <template>
      <div ref="conversation" />
    </template>

    <script>
      ...
      mounted() {
        this.$uikit.render(ConversationContainer, {
            renderSessionListEmpty: () => {
            return compile(`<div>
                < img style = {{ width: '100%' }} src='https://yx-web-nosdn.netease.im/common/2946c48f29d747305e68b1ddf27f3472/无成员可添加@3x.png' />
                <div className='no-session'>暂无会话</div>
            </div> `)}
          }, this.$refs.conversation);
      }
    </script>
    ```
    :::
    ::::::

- 效果对比

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    ---- | ----
    <img alt="会话列表为空时的内容.png" src="https://yx-web-nosdn.netease.im/common/2d6cfd53cee67e303530b9f52cafbfc0/会话列表为空时的内容.png" style="width:100%;border: 1px solid #BFBFBF;"> | <img alt="会话列表为空时内容自定义.png" src="https://yx-web-nosdn.netease.im/common/7d3613f5b613a0e71f07ba13bf60023e/会话列表为空时内容自定义1.png" style="width:100%;border: 1px solid #BFBFBF;">

<a id="自定义会话的展示内容"></a>

### 会话的展示内容

您可自定义会话列表中某个会话对象的头像、昵称以及最后一条消息的展示。

- [查看在线示例](https://codesandbox.io/p/sandbox/zi-ding-yi-hui-hua-de-zhan-shi-nei-rong-8cfj5g)

    在 `IMAppProps` 传入正确的 `appkey`、`account` 和 `token` 即可在线预览效果。

- 示例代码

    :::::: div linked-codes
    ::: code React

    ```JSX/TSX
    import { ComplexAvatarContainer } from '@xkit-yx/im-kit-ui'
    //全局上下文
    const { store } = useStateContext()
    const renderCustomP2pSession = (options) => {
    // 对话方 account
    const conversationPartnerId = options.session.to
    // 对话方个人信息（非好友不返回信息，同步方法）
    const conversationPartnerInfo = store.uiStore.getFriendWithUserNameCard(conversationPartnerId)
    return (
      <div className='session-item' onClick={() => options.onSessionItemClick(options.session)}>
        <ComplexAvatarContainercaccount={conversationPartnerId}>
      <div >
      <div className='nick'>
        {store.uiStore.getAppellation({account: optconversationPartnerId
      </div>
      <div className='msg-body'>
        {options.session.lastMsg.body}
      </div>
      </div></div>
    )
    }
    <ConversationContainer
    renderCustomP2pSession={renderCustomP2pSession}
    ></ConversationContainer>
    ```
    :::
    ::: code Vue2/Vue3

    ```JavaScript/TypeScript
    <template>
      <div ref="conversation" />
    </template>

    <script>
    import { ComplexAvatarContainer } from "@xkit-yx/im-kit-ui";
      ...
        mounted() {
          this.$uikit.render(ConversationContainer, {
                renderCustomP2pSession: (options) => {
                  console.log('==========renderCustomP2pSession===========', options);
                  const { store, nim } = window.__xkit_store__
                  // 对话方 account
                  const conversationPartnerId = options.session.to
                  // 对话方个人信息（非好友不返回信息，同步方法）
                  const conversationPartnerInfo = store.uiStore.getFriendWithUserNameCard(conversationPartnerId)
                  return compile(`<div>
                        <context.ComplexAvatarContainer account='${conversationPartnerId}' />
                        <span>${store.uiStore.getAppellation({ account: conversationPartnerId })}</span>
                      </div>`,
                    { ComplexAvatarContainer })
                }
              }, this.$refs.conversation);
      }
    </script>
    ```
    ::::::

- 示例代码解读

    - `ComplexAvatarContainer` 是 UIKit 的头像组件，传入 `account` 即可展示头像，如用户没有头像就展示昵称后两位。

    - `store.uiStore.getAppellation` 为获取用户展示昵称的方法，按照如下优先级返回：备注 > 群昵称 > 好友昵称 > 好友账号。

    - 上述示例代码的 `const renderCustomP2pSession = (options) => {}` 中，`options` 的定义为 `options: {session: NimKitCoreTypes.ISession} & ConversationCallbackProps) `，其中 `ISession` 和 `ConversationCallbackProps` 的定义如下：

        ```
        type ISession = P2PSession | TeamSession; // 会话类型，P2PSession 表示单聊，TeamSession 表示群聊
        type ConversationCallbackProps = {
            /* 单击事件 */
            onSessionItemClick: (session: NimKitCoreTypes.ISession) => void;
            /* 右键删除事件 */
            onSessionItemDeleteClick: (session: NimKitCoreTypes.ISession) => void;
            /* 右键置顶事件 */
            onSessionItemStickTopChange: (session: NimKitCoreTypes.ISession, isTop: boolean) => void;
            /* 右键静音事件 */
            onSessionItemMuteChange: (session: NimKitCoreTypes.ISession, mute: boolean) => void;
        }
        ```

- 效果对比

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    ---- | ----
    <img alt="会话为单聊时的内容默认 1.png" src="https://yx-web-nosdn.netease.im/common/be310267b9437dc1aedc3b537beefd3d/会话为单聊时的内容默认1.png" style="width:100%;border: 1px solid #BFBFBF;"> | <img alt="会话为单聊时的内容自定义1.png" src="https://yx-web-nosdn.netease.im/common/acb6ac9a5ac5919f9fab1a33df8f0a5c/会话为单聊时的内容自定义1.png" style="width:100%;border: 1px solid #BFBFBF;">

<a id="自定义会话元素"></a>

### 会话元素

可自定义的会话元素包括会话名称、会话消息、单聊会话头像和群聊会话头像。

下文以自定义渲染会话名称为例，介绍的如何在所有会话的名称前都加上 **网易云信** 前缀。

- [查看在线示例](https://codesandbox.io/p/sandbox/zi-ding-yi-hui-hua-yuan-su-6fr97s)

    在 `IMAppProps` 传入正确的 `appkey`、`account` 和 `token` 即可在线预览效果。

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    import { ComplexAvatarContainer } from '@xkit-yx/im-kit-ui'
    //全局上下文
    const { store } = useStateContext()
    const renderSessionName = (options) => {
    const conversationPartnerId = options.session.to
    return (
      <div style={{fontWeight: 'bold'}}>网易云信-{store.uiStore.getAppellation({account: conversationPartnerId})}</div>
    )
    }

    <ConversationContainer
    renderSessionName={renderSessionName}
    ></ConversationContainer>
    ```
    :::
    ::: code Vue2/Vue3
    ```JavaScript/TypeScript
    <template>
      <div ref="conversation" />
    </template>

    <script>
      ...
        mounted() {
          this.$uikit.render(ConversationContainer, {
            renderSessionName: (options) => {
              console.log('==========renderSessionName===========', options);
              const conversationPartnerId = options.session.to
              const { store, nim } = window.__xkit_store__
              const onClick = () => {
                // 自行实现
                this.onSessionItemClick(options);
              };
              return compile(`<div style={{fontWeight: 'bold'}} onClick={context.onClick}>网易云信-${store.uiStore.getAppellation({account: conversationPartnerId})}</div>`,{
                onClick: onClick,
              }
            }
          }, this.$refs.conversation);
        }
    </script>
    ```
    :::
    ::::::

- 效果对比

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    ---- | ----
    <img alt="修改会话名称前 1.png" src="https://yx-web-nosdn.netease.im/common/9cff0a468c2b7c7e190bf75c20386004/修改会话名称前1.png" style="width:100%;border: 1px solid #BFBFBF;"> | <img alt="自定义会话名称 1.png" src="https://yx-web-nosdn.netease.im/common/196ed04736bc797b6d2f5cd777ee4d87/自定义会话名称1.png" style="width:100%;border: 1px solid #BFBFBF;">