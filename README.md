# JJ-loon-config
iOS / tvOS 代理软件 Loon 的配置文件。配置逻辑、策略组和规则顺序参考 [JJ-clash-config](https://github.com/sydneygao/JJ-clash-config)，并转换为 Loon 原生语法。

> Loon 主配置采用 `[General]`、`[Proxy Group]`、`[Rule]` 等 INI 风格分段语法，标准文件扩展名为 `.conf`。

## 1. `JJ-config_full.conf`，含机场订阅的配置文件

### Step 1. 🔗 下载配置文件

**主链路（gh-proxy.org｜最快，≤60 秒更新）：**
```text
https://gh-proxy.org/https://raw.githubusercontent.com/sydneygao/JJ-loon-config/main/JJ-config_full.conf
```

**备链路（gh.idayer.com｜不同链路，实时）：**
```text
https://gh.idayer.com/https://raw.githubusercontent.com/sydneygao/JJ-loon-config/main/JJ-config_full.conf
```

**兜底链路（cdn.jsdelivr.net｜最稳，接受最长约 12 小时延迟）：**
```text
https://cdn.jsdelivr.net/gh/sydneygao/JJ-loon-config@main/JJ-config_full.conf
```

### Step 2. ✈️ 添加机场订阅

找到以下代码，将示例 URL 替换为自己的机场订阅地址：

```text
[Remote Proxy]
Airport1 = https://example.com/your-profile.yaml,parser-enabled=true,udp=true,fast-open=true,enabled=true
```

`parser-enabled=true` 用于调用 Loon 资源解析器处理 Clash / Mihomo 格式的订阅。

不要把包含 Token、用户名或密码的真实订阅地址提交到公开仓库。

### Step 3. ➕ 导入配置

保存修改后的 `JJ-config_full.conf`，然后在 Loon 的配置页面通过本地文件导入。

## 2. `JJ-config.conf`，不含机场订阅的纯配置文件

### Step 1. 🔗 使用链接导入

**主链路（gh-proxy.org｜最快，≤60 秒更新）：**
```text
https://gh-proxy.org/https://raw.githubusercontent.com/sydneygao/JJ-loon-config/main/JJ-config.conf
```

**备链路（gh.idayer.com｜不同链路，实时）：**
```text
https://gh.idayer.com/https://raw.githubusercontent.com/sydneygao/JJ-loon-config/main/JJ-config.conf
```

**兜底链路（cdn.jsdelivr.net｜最稳，接受最长约 12 小时延迟）：**
```text
https://cdn.jsdelivr.net/gh/sydneygao/JJ-loon-config@main/JJ-config.conf
```

### Step 2. ✈️ 单独添加机场订阅

在 Loon 的节点或订阅管理页面单独添加机场订阅。

纯配置中的 `[Remote Filter]` 不绑定特定订阅名称，会从 Loon 中现有的全部本地节点和订阅节点筛选港、日、新、台、美节点；“手动选择”组使用“全部节点”筛选结果。

## 3. 配置说明

- 港、日、新、台、美区域自动测速与手动选择组。
- Google、Apple、Microsoft、AI、社交、游戏、Netflix、Spotify、PayPal 等业务策略。
- 家庭 Wi-Fi 直连，蜂窝网络及其他网络使用规则模式。
- Clash / Mihomo 的 `.mrs` 规则不能直接用于 Loon，已改用 Loon 可识别的远程 `.list` / `.conf` 规则。
- AI 规则组合 SKK 的 AIGC 域名集与 ChatGPT Voice IP 集，并参考 Shadowrocket / Surge 配置补齐 OpenAI、Claude、Gemini、Copilot 的关键依赖域名；共享云服务 ASN 不纳入 AI 策略。
- 儿童保护使用自动更新的 Loon 原生 `category-porn` 规则，并补充 OnlyFans 等核心域名。需要阻止访问时，请在 `Shield` 策略组中选择 `REJECT`。
- Loon 远程规则位于 `[Remote Rule]`；节点筛选使用 `[Remote Filter]` 的 `NameRegex`。
- `IP-CIDR` 与 `IP-ASN` 规则使用 `no-resolve`，减少不必要的 DNS 查询。
- 官方文档：[Loon 使用手册](https://nsloon.app/docs/intro/)
