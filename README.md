# Proxy Rules

一份 **黑名单模式** 的 SwitchyOmega / ZeroOmega 在线规则列表：清单内的域名走代理，其余流量直连。

## 在线规则地址

```
https://raw.githubusercontent.com/ethan42nd/Proxy-Rules/main/proxy-rules.txt
```

规则文件为仓库根目录下的 `proxy-rules.txt`，文件名与上面的地址严格一致，改名需同步修改。

## 覆盖站点

按分类管理，顺序如下：

- **基础服务**：Google / YouTube（搜索、账号登录、视频与图片 CDN）、X（Twitter）、GitHub
- **AI 服务**：OpenAI / ChatGPT / Sora、Claude、xAI / Grok、Perplexity、Cursor、OpenRouter、Notion 等
- **通讯社交**：Telegram、Facebook / Instagram / WhatsApp、Discord、Reddit、LinkedIn
- **流媒体与娱乐**：Netflix、Disney+ / Hulu / HBO Max / Prime Video、Spotify、Twitch、TikTok、Steam
- **知识与其他常用站点**：维基百科、Medium、Quora、Pinterest、Pixiv、Tumblr、Imgur 等
- **R18（成人内容）**：PornHub、Jable、JavDB、iwara、rule34 及其他常见成人站点
- **个人单独规则**（始终放在最后）：沉浸式翻译、`in.mesl.cloud` 单独匹配

## 导入步骤（SwitchyOmega / ZeroOmega 通用）

1. 安装扩展，并先准备一个 **「代理服务器」** 情景模式（填好你自己的代理协议与端口）。
2. 新建情景模式，类型选择 **「自动切换」** （例如命名为 `AutoProxy`），作为日常使用的模式。
3. 在该模式的 **「规则列表设置」** 里点「+ 新增规则列表」：
   - 列表格式：**AutoProxy**
   - 规则列表网址：`https://raw.githubusercontent.com/ethan42nd/Proxy-Rules/main/proxy-rules.txt`
   - 规则匹配时使用的情景模式：选第 1 步建好的代理服务器模式
4. 同一页面底部把 **「默认情景模式」** 设为 **「直接连接」**。
5. 点 **「立即更新规则列表」** ，确认状态显示更新成功且条数不为 0。
6. 点浏览器工具栏上的扩展图标，选用该「自动切换」模式即可。

> raw.githubusercontent.com 有 CDN 缓存，规则更新后可能要等几分钟，或清掉规则列表缓存再点「立即更新规则列表」。

## 维护

- 要加站点，在 `proxy-rules.txt` 对应分组里照现有行的写法加一行即可。
- 改完提交并推送到 `main`，扩展下次自动更新时生效。
- 提交信息格式：`type(scope): 中文描述`。

## 许可

[MIT](./LICENSE)
