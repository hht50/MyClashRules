# MyClashRules

为 Surge、Mihomo 和 OpenClash 维护的个人分流规则集。每份规则描述匹配条件，出口策略由客户端配置决定。

[快速接入](#快速接入) · [规则目录](#规则目录) · [维护说明](#维护说明)

## 常用规则

| 规则集 | 用途 | 订阅地址 |
| --- | --- | --- |
| [飞书 · Lark](Services/Feishu.list) | 飞书中国版和 Lark 国际版 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/Feishu.list) |
| [Apple 推送](Apple/Push.list) | APNs 域名、IPv4 和 IPv6 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Apple/Push.list) |
| [小米互联](Xiaomi/HyperConnect.list) | 实测域名和 IP | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Xiaomi/HyperConnect.list) |
| [越南通用](vngeneral) | 越南地区通用规则 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/vngeneral) |
| [115](Services/115.list) | 115 服务域名 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/115.list) |

## 快速接入

以下以飞书和 Lark 直连为例。复制 Raw 链接，规则优先放在可能提前命中的通用分类及兜底规则之前。

### Surge

在 `[Rule]` 中加入：

```ini
RULE-SET,https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/Feishu.list,DIRECT,update-interval=86400
```

### Mihomo / OpenClash

把 provider 和规则分别合并到现有的 `rule-providers` 和 `rules`。

```yaml
rule-providers:
  feishu-lark:
    type: http
    behavior: classical
    format: text
    url: https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/Feishu.list
    path: ./ruleset/feishu-lark.list
    interval: 86400

rules:
  - RULE-SET,feishu-lark,DIRECT
```

[代理配置仓库](https://github.com/hht50/proxy-client-configs) 提供现有 Mihomo 配置和客户端资料。

## 规则目录

### 办公与设备

| 规则集 | 用途 | 订阅地址 |
| --- | --- | --- |
| [飞书 · Lark](Services/Feishu.list) | 飞书中国版和 Lark 国际版 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/Feishu.list) |
| [Microsoft 直连](Microsoft/Direct.list) | 微软服务例外 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Microsoft/Direct.list) |
| [Parallels 直连](Parallels/Direct.list) | 虚拟机软件服务 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Parallels/Direct.list) |
| [小米互联](Xiaomi/HyperConnect.list) | 实测域名和 IP | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Xiaomi/HyperConnect.list) |
| [达利集团](Services/DaliGroup.list) | 企业服务域名 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/DaliGroup.list) |
| [求职](Jobfind) | 求职站点 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Jobfind) |
| [Copilot](Copilot) | Microsoft Copilot | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Copilot) |
| [AI 服务](ai) | AI 服务分流 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/ai) |

### 通信与推送

| 规则集 | 用途 | 订阅地址 |
| --- | --- | --- |
| [Apple 推送](Apple/Push.list) | APNs 域名、IPv4 和 IPv6 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Apple/Push.list) |
| [极光推送](AppServices/JPush.list) | JPush 服务 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/AppServices/JPush.list) |
| [LINE](LINE) | LINE 服务 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/LINE) |
| [Zalo](zalo.list) | 越南即时通信 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/zalo.list) |
| [Yeetalk](yeetalk.list) | 语言交流应用 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/yeetalk.list) |
| [Meta AI · Muse](Meta/Muse.list) | Muse 和 Meta AI 域名 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Meta/Muse.list) |

### 媒体、游戏与下载

| 规则集 | 用途 | 订阅地址 |
| --- | --- | --- |
| [日本媒体](Media/JapanMedia.list) | 图片与媒体资源 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Media/JapanMedia.list) |
| [TikTok](TIKTOK) | 自维护 TikTok 规则 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/TIKTOK) |
| [SOOP](Soop) | 直播平台 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Soop) |
| [TMDB](TMDB) | 影视元数据 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/TMDB) |
| [Trakt](Trakt) | 影视记录服务 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Trakt) |
| [歌词服务](Services/Lyrics.list) | 歌词相关端点 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/Lyrics.list) |
| [115](Services/115.list) | 115 服务域名 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/115.list) |
| [下载与支付](Services/Download-Payment.list) | 下载与支付相关例外 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/Download-Payment.list) |
| [游戏更新](Gameupdate) | 游戏更新流量 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Gameupdate) |
| [TFT](TFT) | 云顶之弈相关规则 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/TFT) |
| [PUBG](PUBG) | PUBG 相关规则 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/PUBG) |
| [成人媒体](Media/Adu) | 通用版规则 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Media/Adu) |
| [成人媒体 · 越南版](Media/Adu-vietnam.list) | 越南版规则 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Media/Adu-vietnam.list) |

### 地区与网络

| 规则集 | 用途 | 订阅地址 |
| --- | --- | --- |
| [越南通用](vngeneral) | 越南地区通用规则 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/vngeneral) |
| [英国](unitedkingdom) | 英国地区规则 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/unitedkingdom) |
| [俄罗斯](russia.list) | 俄罗斯地区规则 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/russia.list) |
| [韩国](korea.list) | 韩国地区规则 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/korea.list) |
| [新加坡线路](Network/Singapore.list) | 指定使用新加坡线路的主机 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Network/Singapore.list) |
| [IP 直连](Network/Direct-IP.list) | 按目标 IP 匹配的直连例外 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Network/Direct-IP.list) |

### 应用例外与拦截

| 规则集 | 用途 | 订阅地址 |
| --- | --- | --- |
| [字节跳动直连](ByteDance/Direct.list) | 字节跳动服务与 SDK 接口 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/ByteDance/Direct.list) |
| [豆瓣](Services/Douban.list) | 豆瓣域名 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/Douban.list) |
| [酷安](Services/Coolapk.list) | 酷安头像服务 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/Coolapk.list) |
| [Quora](quora.list) | 问答平台 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/quora.list) |
| [官服规则](guanfu.list) | 现有官服分流清单 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/guanfu.list) |
| [反诈规则](Fanzha) | 现有反诈相关清单 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Fanzha) |
| [Apple 广告端点](Apple/Ads-PreMatch.list) | Surge 可在引用行配置预匹配 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Apple/Ads-PreMatch.list) |
| [拦截例外](Overrides/Reject.list) | 广告与追踪端点 | [Raw](https://raw.githubusercontent.com/hht50/MyClashRules/main/Overrides/Reject.list) |

## 维护说明

- [越南通用](vngeneral)用于当前 Mihomo 配置。[vietnam.list](vietnam.list)保留独立条目，合并前逐条核对用途。
- [成人媒体通用版](Media/Adu)为主维护文件。[sese.list](sese.list) 和 [Stash 规则](Stash/Rules/Adu.list) 是兼容入口，通用规则变动时同步核对。
- [台湾 IPv4 清单](dailoanip.list)的来源和生成日期尚未核实。启用前先核对网段归属与更新方式。
- [Gameupdate](Gameupdate)按游戏资源域名匹配。需要补游戏下载节点时，按日志添加具体主机，避免把共享 CDN 的其他业务一起直连。
- [Meta 社交旧清单](facebook.list)含 Facebook、Instagram 和 ASN 匹配，引用前核对客户端支持与策略范围。


- 域名需要连同子域名匹配时使用 `DOMAIN-SUFFIX`，单一主机使用 `DOMAIN`。共用域名（如 `meta.com`）修改前应核对命中顺序。
- 规则统一在 `main`。成人媒体通用版和越南版各用独立文件。[sese.list](sese.list) 以及 `Stash/Overrides/` 下的路径供已有配置继续使用。
- 修改后刷新规则集，用客户端日志检查命中。如果改了 provider 定义、策略或顺序，刷新整份配置。

<details>
<summary>原有 Surge 策略与参数备忘</summary>

| 策略 | 规则与参数 |
| --- | --- |
| `DIRECT` | 小米互联、115、Microsoft、Parallels、字节跳动、酷安。IP 直连带 `no-resolve`，达利集团带 `extended-matching` |
| `Apple 推送` | 本仓库的 APNs 补充清单与 [外部 apns.list](https://github.com/QuixoticHeart/rule-set/blob/ruleset/loon/apns.list)。原组包含香港负载均衡、香港智选和直连 |
| `REJECT` | 拦截例外。Apple 广告端点在 Surge 引用行带 `pre-matching` |
| 地区策略 | 极光推送用香港负载均衡，歌词用香港智选，日本媒体用日本智选，新加坡线路用新加坡智选 |
| `Yellow` | 下载与支付、成人媒体。成人媒体带 `no-resolve` |
| `CELLULAR` | 豆瓣的 Surge iOS 策略，引用带 `extended-matching` |

</details>
