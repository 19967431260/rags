如果默认会话界面（`chat-kit`）无法满足您的业务需求，您可通过聊天组件的自定义参数进行界面自定义。

## 自定义参数

`chat-kit` 提供的自定义参数如下：

| <div style="width:200px">参数</div> | 类型 | 说明 |
| :---- | :---- | :---- |
| `actions` | [`Action[]`](#参数说明) | <p>消息发送按钮组配置，不传使用默认的配置</p><ul><li>action: 按钮类型，内置类型包括表情(`emoji`）、发送图片（`sendImg`）、发送文字（`sendMsg`）和发送文件（`sendFile`），如需自定义请使用自定义 action 名称</li><li> visible：boolean 类型，是否显示该按钮，默认 true</li><li>render: ` (props: ActionRenderProps) => ReactNode}` 类型，自定义渲染，如果不传则使用默认渲染方</li></ul><br>具体的示例参考下文 [自定义消息发送按钮](#自定义消息发送按钮)。 |
| `renderP2pInputPlaceHolder`     | ((session: [Session](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.NIMSession.html)) => string) | 自定义渲染单聊聊天输入框 placeholder，具体的示例参考下文 [自定义输入框 placeholder](#自定义输入框-placeholder)。 |
| `renderTeamInputPlaceHolder` | ((params: { session: [Session](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.NIMSession.html); mute: boolean; }) => string) | 自定义渲染群组聊天输入框 placeholder，具体的示例参考下文 [自定义输入框 placeholder](#自定义输入框-placeholder)。 |
| `renderTeamMemberItem` | `((params: { member: TeamMember & Partial<FriendProfile>; }) => Element | null)` | 自定义渲染 [群组成员 item](#群成员-item)。<note type="note">member 的类型请参考 [TeamMember](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_TeamInterface.NIMTeamMember.html)。</note> |
| `onSendText` | `((data: { value: string; scene: "p2p" | "team" | "superTeam"; to: string; }) => Promise<void>)`     | 发送文字消息的回调，一般用于默认的文字发送缺少想要的字段时。具体使用示例参考 [实现自定义消息收发](https://doc.yunxin.163.com/messaging-uikit/guide/jA0NjExNTg?platform=web)。 |
| `afterTransferTeam` | (teamId: string) => Promise<void> | 转让群主后的回调。
| `renderP2pCustomMessage` | `((options: RenderP2pCustomMessageOptions) => Element | null)` | 渲染单聊中的自定义消息。 |
| `renderTeamCustomMessage`     | `((options: RenderTeamCustomMessageOptions) => Element | null)` | 渲染群聊中的自定义消息 <note type="note">RenderTeamCustomMessageOptions.msg 的类型请参考 [IMMessage](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.NIMMessage.html)。</note> |
| `renderEmpty` | (() => Element) | 自定义渲染未选中任何会话时的内容，具体示例参考下文 [自定义未选中会话时的内容](#自定义未选中会话时的内容)。 |
| `renderHeader` | ((session: [Session](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_SessionInterface.NIMSession.html)) => Element) | 自定义渲染会话的 header 样式，具体示例参考下文 [自定义会话 header 渲染](#自定义会话-header-渲染)。 |
| `selectedSession` | string | 自定义选中的会话 sessionId，若为群聊场景，则填入 `team-teamId`。若为单聊场景，则填入 `p2p-accountId`。一般不用传，内部会处理好选中逻辑。 |
| `prefix` | string | 样式前缀，默认值：`chat`。 |
| `commonPrefix` | string | 公共样式前缀，默认值：`common`。 |
| `renderMessageOuterContent` | `((msg: IMMessage) => JSX.Element | null | undefined)` | 自定义渲染会话消息，气泡样式也需要自定义，具体示例参考下文 [自定义渲染消息体](#自定义渲染消息体)。<note type="note">msg 的类型请参考 [IMMessage](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.NIMMessage.html)。</note> |
| `renderMessageInnerContent` | `((msg: IMMessage) => JSX.Element | null | undefined)` | 自定义渲染会话消息，不需要自定义气泡样式，具体示例参考下文 [自定义渲染消息体](#自定义渲染消息体)。<note type="note">msg 的类型请参考 [IMMessage](https://doc.yunxin.163.com/docs/interface/messaging/web/typedoc/Latest/zh/NIM/interfaces/nim_MessageInterface.NIMMessage.html)。</note> |
| `msgOperMenu` | [`MsgOperMenuItem[]`](#参数说明) | 自定义渲染消息右键菜单，包括菜单项是否显示（show）、菜单项名称（label、key、icon）、自定义单击事件（onClick），具体示例参考下文 [自定义消息右键操作列表](#自定义消息右键操作列表)。
| [`p2pSettingActions`](#参数说明) | ChatSettingActionItem[] | 自定义单聊消息页面右侧的设置栏按钮，具体示例参考下文 [自定义消息页面右侧设置栏按钮](#自定义消息页面右侧设置栏按钮)。
| `teamSettingActions` | ChatSettingActionItem[] | 自定义群聊消息页面右侧的设置栏按钮，具体示例参考下文 [自定义消息页面右侧设置栏按钮](#自定义消息页面右侧设置栏按钮)。
| `scrollIntoMode` | `nearest` | 上拉加载消息滚动模式。组件在上拉加载消息时，默认会自动滚动到最新的消息，当组件位于可滚动的页面中时，可能会造成滚动异常，设置 nearest 即可。

:::note note
- 对于单聊消息体的自定义渲染，若同时设置了 `renderP2pCustomMessage`、`renderMessageOuterContent` 和 `renderMessageInnerContent`，那么会按照一下优先级进行修改：renderP2pCustomMessage > renderMessageOuterContent> renderMessageInnerContent。

- 同理，对于群聊消息体的自定义渲染，优先级为：renderTeamCustomMessage > renderMessageOuterContent> renderMessageInnerContent。
:::

## 自定义示例

<a id="自定义渲染消息体"></a>

### 渲染消息体

在单聊界面，自定义渲染消息体（区分是否自定义气泡样式）。

- 自定义渲染消息体（需要自定义气泡样式）的示例代码：

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    const renderMessageOuterContent = (msg) => {
        const msgText = msg.text
        return(
            <div style={{backgroundColor:'burlywood', margin:'20px'}}>
            { msgText }
            </div>
        )
        }

        <ChatContainer
            // ...
            renderMessageOuterContent={renderMessageOuterContents}
        />
    ```
    :::
    ::: code Vue2/Vue3
    ```TypeScript
    <template>
        <div ref="chat" />
    </template>

    <script>
        ...
            mounted() {
                this.$uikit.render(
                    ChatContainer,
                    {
                    renderMessageOuterContent: (msg) => {
                        const msgText = msg.text
                        return compile(
                        `<div style={{backgroundColor:'burlywood', margin:'20px'}}>
                            { context.msgText }
                        </div>`, { msgText })
                    }
                    },
                    this.$refs.chat
                );
            }
    </script>
    ```
    :::
    ::::::

- 自定义渲染消息体（不需要自定义气泡样式）的示例代码：

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    const renderMessageInnerContent = (msg) => {
        const msgText = msg.text
        return(
            <div style={{backgroundColor:'burlywood', margin:'20px'}}>
            { msgText }
            </div>
        )
        }

        <ChatContainer
            // ...
            renderMessageInnerContent={renderMessageInnerContent}
        />
    ```
    :::
    ::: code Vue2/Vue3
    ```TypeScript
    <template>
        <div ref="chat" />
    </template>

    <script>
        ...
            mounted() {
                this.$uikit.render(
                    ChatContainer,
                    {
                    renderMessageInnerContent: (msg) => {
                        const msgText = msg.text
                        return compile(
                        `<div style={{backgroundColor:'burlywood', margin:'20px'}}>
                            { context.msgText }
                        </div>`, { msgText })
                    }
                    },
                    this.$refs.chat
                );
            }
    </script>
    ```
    :::
    ::::::

- 效果比对

    默认消息体 | 自定义渲染消息体（需要自定义气泡样式） | 自定义渲染消息体（不需要自定义气泡样式）
    :---- | :----
    <img alt="Web 默认消息体.png" src="https://yx-web-nosdn.netease.im/common/67a741ea9bd43966c4f12c1438101ea9/Web默认消息体.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="渲染消息体out.png" src="https://yx-web-nosdn.netease.im/common/ed4cdc6d118b1faa493534e4df8063d4/渲染消息体out.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="渲染消息体in.png" src="https://yx-web-nosdn.netease.im/common/79085b7b4305af7e0f378a697e42f2a2/渲染消息体in.png" style="width:80%;border: 1px solid #BFBFBF;">


<a id="自定义消息发送按钮"></a>

### 消息发送按钮

本节提供以下示例供您参考：

- [示例 1](#示例-1)：将默认的消息发送按钮删除，并新增一个自定义的消息发送按钮。
- [示例 2](#示例-2)：在保留默认的消息发送按钮的基础上，新增一个自定义的消息发送按钮。
- [查看在线示例](https://codesandbox.io/p/sandbox/zi-ding-yi-xiao-xi-fa-song-an-niu-5cjkpg)

    在 `IMAppProps` 传入正确的 `appkey`、`account` 和 `token` 即可在线预览效果。

<a id="示例-1"></a>

**示例一**

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    import { ComplexAvatarContainer } from '@xkit-yx/im-kit-ui'
    //全局上下文
    const { store } = useStateContext()
    const actions = [
        {
            action: 'emoji',
            visible: true,
            render: () => {
            return (
                //绑定的事件中可以从 store 中访问上下文
                <div style={{margin: '0 10px'}}>
                <i className="iconfont seeting">&#xe6d6;</i>
                </div>
            )
            }
        }
    ]

    <ChatContainer
        ...
        actions={actions}
        />
    ```
    :::
    ::: code Vue2/Vue3
    ```TypeScript
    <template>
        <div ref="chat" />
    </template>

    <script>
        ...
            mounted() {
                this.$uikit.render(
                ChatContainer,
                {
                actions:[{
                    action: 'emoji',
                    visible: true,
                    render: () => {
                    return compile(
                        `<div style={{margin: '0 10px'}}>
                        <i className="iconfont icon-logout" />
                        </div>`
                    )
                    }
                }]
                },
                this.$refs.chat
            );
            }
    </script>
    ```
    :::
    ::::::

- 效果比对

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="消息发送按钮.png" src="https://yx-web-nosdn.netease.im/common/4dedb667bd30a477f8219a2cc63abb85/消息发送按钮.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="删除默认增加自定义按钮 1.png" src="https://yx-web-nosdn.netease.im/common/1fb3399fe33636101a24e1bf43b527a9/删除默认增加自定义按钮1.png" style="width:80%;border: 1px solid #BFBFBF;">

<a id="示例-2"></a>

**示例二**

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    import { ComplexAvatarContainer } from '@xkit-yx/im-kit-ui'
    //全局上下文
    const { store } = useStateContext()
    const actions = [
        {
        action: 'setting',
        visible: true,
        render: () => {
            return (
            <div style={{margin: '0 10px', fontSize: '14px'}}>
                <i style={{ fontSize: '14px'}} className="iconfont seeting">&#xe6d6;</i>
            </div>
            )
        }
        },
        {
        action: 'emoji',
        visible: true,
        },
        {
        action: 'sendImg',
        visible: true,
        },
        {
        action: 'sendFile',
        visible: true,
        },
        {
        action: 'sendMsg',
        visible: true,
        }
    ]

    <ChatContainer
        ...
        actions={actions}
        />
    ```
    :::
    ::: code Vue2/Vue3
    ```TypeScript
    <template>
        <div ref="chat" />
    </template>

    <script>
        ...
            methods: {
            sendMsg() {
                console.log('==========sendMsg===========');
            }
            },
            mounted() {
                this.$uikit.render(
                ChatContainer,
                {
                actions: [
                    {
                    action: 'setting',
                    visible: true,
                    render: () => {
                        return compile(
                        `<div onClick={context.sendMsg} style={{margin: '0 10px', fontSize: '14px'}}>
                            <i className="iconfont icon-logout" />
                        </div>`, { sendMsg: this.sendMsg })
                    }
                    },
                    {
                    action: 'emoji',
                    visible: true,
                    },
                    {
                    action: 'sendImg',
                    visible: true,
                    },
                    {
                    action: 'sendFile',
                    visible: true,
                    },
                    {
                    action: 'sendMsg',
                    visible: true,
                    }
                ]
                },
                this.$refs.chat
            );
            }
    </script>
    ```
    :::
    ::::::

- 效果比对

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="消息发送按钮.png" src="https://yx-web-nosdn.netease.im/common/4dedb667bd30a477f8219a2cc63abb85/消息发送按钮.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="新增按钮保留默认 1.png" src="https://yx-web-nosdn.netease.im/common/4ba7b9ce5a9afe1888d7badca886615f/新增按钮保留默认1.png" style="width:80%;border: 1px solid #BFBFBF;">

<a id="自定义输入框-placeholder"></a>

### 输入框 placeholder

- [查看在线示例](https://codesandbox.io/p/sandbox/zi-ding-yi-shu-ru-kuang-placeholder-xkwr4l)

    在 `IMAppProps` 传入正确的 `appkey`、`account` 和 `token` 即可在线预览效果。

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    import { ComplexAvatarContainer } from '@xkit-yx/im-kit-ui'
    //全局上下文
    const { store } = useStateContext()
    const renderP2pInputPlaceHolder = (options) => {
        return `发送给${store.uiStore.getAppellation({account: options.to})}`
    }

    <ChatContainer
        ...
        renderP2pInputPlaceHolder={renderP2pInputPlaceHolder}
        />
    ```
    :::
    ::: code Vue2/Vue3
    ```TypeScript
    <template>
        <div ref="chat" />
    </template>

    <script>
        ...
            mounted() {
                this.$uikit.render(
                ChatContainer,
                {
                renderP2pInputPlaceHolder :(options) => {
                    const { store, nim } = window.__xkit_store__
                    return `发送给${store.uiStore.getAppellation({account: options.to})}`
                }
                },
                this.$refs.chat
            );
            }
    </script>
    ```
    :::
    ::::::

- 效果比对

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="默认的输入框 placeholder.png" src="https://yx-web-nosdn.netease.im/common/4b5631201e1fd738035474060d3f9e25/默认的输入框placeholder.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="自定义输入框 placeholder1.png" src="https://yx-web-nosdn.netease.im/common/b9d076293c1cae0bae622fdb9894b9d3/自定义输入框placeholder1.png" style="width:80%;border: 1px solid #BFBFBF;">

<a id="自定义未选中会话时的内容"></a>

### 未选中会话时的内容

- [查看在线示例](https://codesandbox.io/p/sandbox/zi-ding-yi-wei-xuan-zhong-hui-hua-shi-de-nei-rong-j8h59q)

    在 `IMAppProps` 传入正确的 `appkey`、`account` 和 `token` 即可在线预览效果。

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    const renderEmpty = () => {
        return (
        <div>
            <img className='empty' src='https://yx-web-nosdn.netease.im/common/2946c48f29d747305e68b1ddf27f3472/无成员可添加@3x.png'/>
        </div>
        )
    }

        <ChatContainer
        ...
        renderEmpty={renderEmpty}
        />
    ```
    :::
    ::: code Vue2/Vue3
    ```TypeScript
    <template>
        <div ref="chat" />
    </template>

    <script>
        ...
            mounted() {
                this.$uikit.render(
                ChatContainer,
                {
                renderEmpty: () => {
                    return compile(
                    `<div>
                        <img className='empty' src='https://yx-web-nosdn.netease.im/common/2946c48f29d747305e68b1ddf27f3472/无成员可添加@3x.png'/>
                    </div>`
                    )
                }
                },
                this.$refs.chat
            );
            }
    </script>
    ```
    :::
    ::::::

- 效果对比

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="未选中会话时的默认展示.png" src="https://yx-web-nosdn.netease.im/common/b79a6582d123eb7f6f13448393aa9f5f/未选中会话时的默认展示.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="未选中会话时的默认展示自定义后1.png" src="https://yx-web-nosdn.netease.im/common/f5a5d6ae964e68d0dc1f82212cc874c2/未选中会话时的默认展示自定义后1.png" style="width:80%;border: 1px solid #BFBFBF;">

<a id="自定义会话-header-渲染">

### 会话 header 渲染

- [查看在线示例](https://codesandbox.io/p/sandbox/zi-ding-yi-hui-hua-header-xuan-ran-yhln27)

    在 `IMAppProps` 传入正确的 `appkey`、`account` 和 `token` 即可在线预览效果。

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    const [teamInfo, setTeamInfo] = useState({})
        const renderHeader = (options) => {
        store.teamStore.getTeamForceActive(options.to).then(res => {
            setTeamInfo(res)
        })
        return (
        <div style={{display: 'flex', alignItems: 'center'}}>
            <img className='avatar' src={teamInfo.avatar} alt="" />
            <div style={{fontWeight: 'bold'}}>网易云信-{teamInfo.name}-自定义</div>
        </div>)
        }
    ```
    :::
    ::: code Vue2/Vue3
    ```TypeScript
    <template>
        <div ref="chat" />
    </template>

    <script>
        ...
        data: function () {
            return {
            };
            },
            methods: {
            sendMsg() {
                console.log('==========sendMsg===========');
            }
            },
            mounted() {
                this.$uikit.render(
                ChatContainer,
                {
                renderHeader :(options) => {
                    console.log('==========renderHeader===========', options);
                    const { store, nim } = window.__xkit_store__
                    const teamInfo = store.teamStore.teams.get(options.to)
                    return compile(
                    `<div onClick={context.sendMsg} style={{display: 'flex', alignItems: 'center'}}>
                    <img className='avatar' src={context.teamInfo.avatar} />
                    <div style={{fontWeight: 'bold'}}>网易云信-{context.teamInfo.name}-自定义</div>
                    </div>`, { teamInfo: teamInfo, sendMsg: this.sendMsg })
                }
                },
                this.$refs.chat
            );
            }
    </script>
    ```
    :::
    ::::::

- 效果对比

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="默认会话 header 渲染.png" src="https://yx-web-nosdn.netease.im/common/dd23e0c971a946b28f3166516b748b17/默认会话header渲染.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="会话 header 渲染自定义后 1.png" src="https://yx-web-nosdn.netease.im/common/bb35489ef56f167b6d7ee70c7efbd2bb/会话header渲染自定义后1.png" style="width:80%;border: 1px solid #BFBFBF;">

<a id="自定义消息右键操作列表"></a>

### 消息右键操作列表

本节提供三个示例供您参考

- [新增复制操作](#新增复制操作)：在原有菜单基础上新增一项 **复制** 操作。
- [移除原有操作项](#移除原有操作项)：移除原有消息操作菜单相关配置项，例如不希望消息可以 **删除** 或者 **撤回**。
- [替换操作项的样式](#替换操作项的样式)：对原有消息菜单操作配置项进行自定义渲染和自定义单击事件，例如替换 **删除** 消息的文字和 icon。

**新增复制操作**

在原有的消息右键菜单基础上新增一项 **复制** 操作。

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    const menuItems = [
        {
            key: 'recall',
        },
        {
            key: 'reply',
        },
        {
            key: 'delete',
        },
        {
            key: 'forward',
        },
        {
            key: 'copy',
            icon: <CopyOutlined />,
            label: '复制',
            show: 1,
            onClick: (msg) => {
            console.log('========msg========', msg)
            // do something
            },
        },
        ]

        <ChatContainer
            //...
            msgOperMenu={menuItems}
        />
    ```
    :::
    ::: code Vue2/Vue3
    ```TypeScript
    <template>
        <div ref="chat" />
    </template>

    <script>
        ...
            mounted() {
                this.$uikit.render(
                ChatContainer,
                {
                msgOperMenu:[
                    {
                    key: 'recall',
                    },
                    {
                    key: 'reply',
                    },
                    {
                    key: 'delete',
                    },
                    {
                    key: 'forward',
                    },
                    {
                    key: 'copy',
                    icon: compile(`<i className="iconfont icon-logout" />`),
                    label: '复制',
                    show: 1,
                    onClick: (msg) => {
                        console.log('========msg========', msg)
                        // do something
                    },
                    },
                ]
                },
                this.$refs.chat
            );
            }
    </script>
    ```
    :::
    ::::::

- 效果比对

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="web 消息右键默认.png" src="https://yx-web-nosdn.netease.im/common/9bd2ea226748faa83fbd486cd1169b80/web消息右键默认.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="web 消息右键复制.png" src="https://yx-web-nosdn.netease.im/common/609e6a728860e3459c7a3c8dbcba32c5/web消息右键复制.png" style="width:80%;border: 1px solid #BFBFBF;">

**移除原有操作项**

移除原有消息操作菜单相关配置项，例如不希望消息可以 **删除** 或者 **撤回**。

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    const menuItems = [
        {
            key: 'recall',
            show: 0,
        },
        {
            key: 'reply',
        },
        {
            key: 'delete',
            show: 0,
        },
        {
            key: 'forward',
        },
        ]

        <ChatContainer
            //...
            msgOperMenu={menuItems}
        />
    ```
    :::
    ::: code Vue2/Vue3
    ```TypeScript
    <template>
        <div ref="chat" />
    </template>

    <script>
        ...
            mounted() {
                this.$uikit.render(
                ChatContainer,
                {
                msgOperMenu:[
                    {
                        key: 'recall',
                        show: 0,
                    },
                    {
                        key: 'reply',
                    },
                    {
                        key: 'delete',
                        show: 0,
                    },
                    {
                        key: 'forward',
                    },
                    ]
                },
                this.$refs.chat
            );
            }
    </script>
    ```
    :::
    ::::::

- 效果比对

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="web 消息右键默认.png" src="https://yx-web-nosdn.netease.im/common/9bd2ea226748faa83fbd486cd1169b80/web消息右键默认.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="web 消息右键删除.png" src="https://yx-web-nosdn.netease.im/common/471a83af842b9f40ce0d0cfdfd52136c/web消息右键删除.png" style="width:80%;border: 1px solid #BFBFBF;">

**替换操作项的样式**

对原有消息菜单操作配置项进行自定义渲染和自定义单击事件，例如替换 **删除** 消息的文字和图标（icon）。

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    const menuItems = [
        {
            key: 'recall',
        },
        {
            key: 'reply',
        },
        {
            key: 'delete',
            icon: <FileExcelOutlined />,
            label: 'delete',
            show: 1,
            onClick: (msg) => {
            console.log('========msg========', msg)
            // do something
            },
        },
        {
            key: 'forward',
        },
        ]

        <ChatContainer
            //...
            msgOperMenu={menuItems}
        />
    ```
    :::
    ::: code Vue2/Vue3
    ```TypeScript
    <template>
        <div ref="chat" />
    </template>

    <script>
        ...
            mounted() {
                this.$uikit.render(
                ChatContainer,
                {
                msgOperMenu: [
                    {
                    key: 'recall',
                    },
                    {
                    key: 'reply',
                    },
                    {
                    key: 'delete',
                    icon: compile(`<i className="iconfont icon-logout" />`),
                    label: 'delete',
                    show: 1,
                    onClick: (msg) => {
                        console.log('========msg========', msg)
                        // do something
                    },
                    },
                    {
                    key: 'forward',
                    },
                ]
                },
                this.$refs.chat
            );
            }
    </script>
    ```
    :::
    ::::::

- 效果比对

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="web 消息右键默认.png" src="https://yx-web-nosdn.netease.im/common/9bd2ea226748faa83fbd486cd1169b80/web消息右键默认.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="web 消息右键自定义.png" src="https://yx-web-nosdn.netease.im/common/3f7bb1427e695f3ba5f124b80b7a6900/web消息右键自定义.png" style="width:80%;border: 1px solid #BFBFBF;">

<a id="自定义消息页面右侧设置栏按钮"></a>

### 消息页面右侧设置栏按钮

**单聊消息页面** 和 **群聊消息页面** 的右侧设置栏可以自定义按钮。

本文提供 **在单聊消息页面隐藏原有的设置按钮, 并在右侧设置栏新增一个按钮** 的示例供您参考。

- 示例代码

    :::::: div linked-codes
    ::: code React
    ```JSX/TSX
    //若需要在群聊消息页面设置，将 p2pSettingActions 替换为 teamSettingActions 即可
    const p2pSettingActions = [
        {
            action: 'chatSetting',
            visible: false,
        },
        {
            action: 'chatHistory',
            visible: true,
            render: () => {
            //todo
            return <i className="iconfont">&#xe6c9;</i>
            },
            onClick: () => {
            //todo
            },
        },
        ]

        <ChatContainer
            //...
            p2pSettingActions={p2pSettingActions}
        />
    ```
    :::
    ::: code Vue2/Vue3
    ```JSX/TSX
    <template>
        <div ref="chat" />
    </template>

    <script>
        mounted() {
            this.$uikit.render(
            ChatContainer,
            {
                teamSettingActions: [
                {
                    action: 'chatSetting',
                    visible: false,
                },
                {
                    action: 'chatHistory',
                    visible: true,
                    render: () => {
                    //todo
                    return compile(`<i className="iconfont">&#xe6c9;</i>`)
                    },
                    onClick: () => {
                    //todo
                    },
                },
                ]
            },
            this.$refs.chat
            );
        }
        ...
    </script>
    ```
    :::
    ::::::

- 效果比对

    <div style="width:50%">默认</div> | <div style="width:50%">自定义后</div>
    :---- | :----
    <img alt="消息页面右侧按钮.png" src="https://yx-web-nosdn.netease.im/common/e211eb1e6b76c5355aa0f1be57db96c0/消息页面右侧按钮.png" style="width:80%;border: 1px solid #BFBFBF;"> | <img alt="消息页面右侧按钮自定义.png" src="https://yx-web-nosdn.netease.im/common/7c6b9314870d6802a1326c6bbdb1a4e2/消息页面右侧按钮自定义.png" style="width:80%;border: 1px solid #BFBFBF;">

## 图例参考

<a id="群成员-item"></a>

**群成员 Item**

<img style="width:80%" src="https://yx-web-nosdn.netease.im/common/ec70ab4e4a8db5fd71ff799286390256/群成员Item.png" />

**已读未读标记**

<img alt="Web 单聊已读未读标记.png" src="https://yx-web-nosdn.netease.im/common/d574c30d00329a5a563b658c91b499fb/Web单聊已读未读标记.png" style="width:80%;border: 1px solid #BFBFBF;">

**消息右键操作菜单**

<img style="width:50%" src="https://yx-web-nosdn.netease.im/common/9bd2ea226748faa83fbd486cd1169b80/web消息右键默认.png" />

<a id="参数说明"></a>

## 参数说明

- `Action`：

    ```JavaScript
    interface Action {
    /**
        按钮类型
        */
    action: 'emoji' | 'sendImg' | 'sendFile' | 'sendMsg' |string
    /**
        是否显示该按钮，自带按钮默认 true，新增自定义按钮默认 false
        */
    visible?: boolean
    /**
        自定义渲染，如果不传则使用默认渲染方式
        */
    render?: (props: ActionRenderProps) => ReactNode
    }
    ```

- `MsgOperMenuItem`：

    ```JavaScript
    interface MsgOperMenuItem {
    // 是否显示
    show?: 1 | 0
    // 名称
    label?: string
    // 唯一 key
    key: MenuItemKey
    // 图标
    icon?: React.ReactNode
    onClick?: (msg: IMMessage) => void
    }
    ```

- `p2pSettingActions`：

    ```JavaScript
    interface MsgOperMenuItem {
    // 唯一 key
    action: 'chatSetting' | 'chatRecord' | string
    // 是否显示，自带按钮默认 true，新增自定义按钮默认 false
    visible?: boolean
    // 自定义渲染函数
    render?: () => JSX.Element
    onClick?: () => void
    }
    ```