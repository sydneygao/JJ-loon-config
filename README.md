# JJ-loon-config

iOS / tvOS 代理软件 Loon 的个人配置文件，配置逻辑、策略组和规则顺序参考 [`JJ-clash-config`](https://github.com/sydneygao/JJ-clash-config)，并转换为 Loon 原生语法。

## 配置文件

`JJ-config.yaml` 包含：

- 港、日、新、台、美区域自动测速与手动选择组
- Google、Apple、Microsoft、AI、社交、游戏、Netflix、Spotify、PayPal 等业务策略
- 家庭 Wi-Fi 直连与蜂窝网络规则模式切换
- Loon 原生 DNS、Real IP、远程节点筛选及远程规则配置
- 与 `JJ-clash-config` 对齐的自定义域名和 ASN 补充规则

> Loon 的配置内容采用 `[General]`、`[Proxy Group]`、`[Rule]` 等 INI 风格分段语法，并不是 YAML。文件名 `JJ-config.yaml` 按本仓库约定保留。

## 使用方法

### 1. 设置机场订阅

下载 `JJ-config.yaml`，找到以下内容：

```text
[Remote Proxy]
Airport1 = https://example.com/your-profile.yaml,parser-enabled=true,udp=true,fast-open=true,enabled=true
```

将示例 URL 替换为你自己的机场订阅地址。不要把包含 Token、用户名或密码的真实订阅地址提交到公开仓库。

### 2. 导入 Loon

在 Loon 的配置页面使用 URL 下载或导入修改后的本地文件。

原始链接：

```text
https://raw.githubusercontent.com/sydneygao/JJ-loon-config/main/JJ-config.yaml
```

中国大陆加速链接：

```text
https://cdn.jsdelivr.net/gh/sydneygao/JJ-loon-config@main/JJ-config.yaml
```

```text
https://git.yylx.win/raw.githubusercontent.com/sydneygao/JJ-loon-config/main/JJ-config.yaml
```

## 说明

- Clash / Mihomo 的 `.mrs` 规则集不能直接用于 Loon；本配置改用 Loon 可识别的纯文本 `.list` 规则。
- Loon 的远程规则必须放在 `[Remote Rule]`，不能照搬 Clash 的 `rule-providers` / `RULE-SET` 结构。
- 节点筛选使用 `[Remote Filter]` 的 `NameRegex`，再由 `[Proxy Group]` 引用。
- `IP-CIDR` 与 `IP-ASN` 规则使用 `no-resolve`，减少不必要的 DNS 查询。
- 官方文档：[Loon 使用手册](https://nsloon.app/docs/intro/)
