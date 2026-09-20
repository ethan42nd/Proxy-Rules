# Proxy Rules

一份**白名单（清单）模式**的 SwitchyOmega 在线规则列表：只有清单内的域名走代理，其余流量一律直连。

## 在线规则地址

```
https://raw.githubusercontent.com/ethan42nd/Proxy-Rules/main/proxy-rules.txt
```

对应仓库文件：`proxy-rules.txt`（规则文件名与上面的地址严格一致，改名需同步修改此处）。

## 规则模式说明

- 采用 AutoProxy 兼容语法，主要为 `||example.com^` 通配写法，自动覆盖该域名及其全部子域。
- 清单内已包含各站点必要的 CDN：Google / YouTube（账号登录、搜索、视频、图片）、X（含短链与媒体 CDN）、GitHub，以及 `in.mesl.cloud`。
- `in.mesl.cloud` 为**精确匹配**（`|https://in.mesl.cloud^`），不代理其任何子域。
- 白名单语义由 SwitchyOmega 侧配置实现：命中规则 → 代理，未命中 → 直连（默认情景模式设为「直接连接」）。

## SwitchyOmega 导入步骤

1. 安装 SwitchyOmega（Chrome / Edge 扩展），并先准备好一个**「代理服务器」**情景模式（填好你自己的代理协议、地址与端口，例如本机 Clash 的 HTTP 端口）。
2. 新建情景模式 → 类型选择**「自动切换」**（例如命名为 `AutoProxy`），作为日常使用的模式。
3. 在该「自动切换」模式页面找到**「规则列表设置」** → 「+ 新增规则列表」：
   - 列表格式：**AutoProxy**
   - 规则列表网址：`https://raw.githubusercontent.com/ethan42nd/Proxy-Rules/main/proxy-rules.txt`
   - 规则匹配时使用的情景模式：**选择第 1 步建好的代理服务器模式**
4. 同一页面底部把**「默认情景模式」设为「直接连接」**——这一步就是白名单的关键，未命中规则的请求全部直连。
5. 点击**「立即更新规则列表」**，确认列表状态显示更新成功且条数不为 0。
6. 点击浏览器工具栏 SwitchyOmega 图标，选用该「自动切换」模式即可。

> 提示：raw.githubusercontent.com 有 CDN 缓存，规则更新后可能需要等几分钟，或清掉规则列表缓存再点「立即更新规则列表」。若浏览器无法访问该地址，请先确认 raw.githubusercontent.com 本身可直连，或改用 GitHub 镜像前缀。

## 修改与维护

- 新增站点：在 `proxy-rules.txt` 对应分组下加一行 `||example.com^`（自动包含子域）。
- 只代理单个主机、不含子域：用 `|https://example.com^`（必要时再加一行 `|http://...`）。
- 想让某个域名强制直连（即便被通配覆盖）：加一行 `@@||example.com^`。
- 修改后提交并推送到 `main`，SwitchyOmega 下次自动更新时即生效。
- 提交信息格式：`type(scope): 中文描述`，例如 `feat(rules): 新增 GitHub Copilot 域名`。

## 许可

[MIT](./LICENSE)
