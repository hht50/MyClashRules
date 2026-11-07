# MyClashRules

个人分流规则集。新规则按服务或用途归档，策略和规则顺序由引用它们的配置决定。

## 目录索引

### [Apple/](Apple) · Apple 服务例外

| 文件 | 用途 | 当前 Surge 策略 |
| --- | --- | --- |
| [Push.list](Apple/Push.list) | Apple 推送通知服务（APNs）的补充清单，含域名、IPv4 和 IPv6 | `Apple 推送`（香港负载均衡、香港智选、直连） |
| [外部 apns.list](https://github.com/QuixoticHeart/rule-set/blob/ruleset/loon/apns.list) | Apple 推送通知服务（APNs）。用于系统和 App 的通知推送，主要域名为 `*.push.apple.com` | `Apple 推送`（香港负载均衡、香港智选、直连） |
| [Ads-PreMatch.list](Apple/Ads-PreMatch.list) | Apple 广告端点，预匹配标志放在 Surge 引用行 | `REJECT + pre-matching` |

### [Microsoft/](Microsoft) · 微软服务例外

| 文件 | 用途 | 当前 Surge 策略 |
| --- | --- | --- |
| [Direct.list](Microsoft/Direct.list) | Microsoft 域名直连 | `DIRECT` |

### [Parallels/](Parallels) · Parallels 服务例外

| 文件 | 用途 | 当前 Surge 策略 |
| --- | --- | --- |
| [Direct.list](Parallels/Direct.list) | Parallels 域名直连 | `DIRECT` |

### [ByteDance/](ByteDance) · 字节跳动服务例外

| 文件 | 用途 | 当前 Surge 策略 |
| --- | --- | --- |
| [Direct.list](ByteDance/Direct.list) | 字节跳动域名及 SDK 接口直连 | `DIRECT` |

### [AppServices/](AppServices) · 推送与应用服务

| 文件 | 用途 | 当前 Surge 策略 |
| --- | --- | --- |
| [JPush.list](AppServices/JPush.list) | 极光推送 | `🇭🇰香港负载均衡` |

### [Network/](Network) · 按 IP 或线路维护的例外

| 文件 | 用途 | 当前 Surge 策略 |
| --- | --- | --- |
| [Direct-IP.list](Network/Direct-IP.list) | 直连网段，100.65.48.0/24 是标准网络地址 | `DIRECT + no-resolve` |
| [Singapore.list](Network/Singapore.list) | 指定使用新加坡线路的主机 | `🇸🇬 新加坡智选` |

### [Services/](Services) · 按应用或用途维护的规则

| 文件 | 用途 | 当前 Surge 策略 |
| --- | --- | --- |
| [115.list](Services/115.list) | 115 服务，根域后缀覆盖子域名 | `DIRECT` |
| [Lyrics.list](Services/Lyrics.list) | 歌词服务端点 | `🇭🇰香港智选` |
| [Download-Payment.list](Services/Download-Payment.list) | 下载与支付相关域名，保留原分流 | `Yellow` |
| [DaliGroup.list](Services/DaliGroup.list) | 达利集团域名 | `DIRECT + extended-matching` |
| [Douban.list](Services/Douban.list) | 豆瓣域名，CELLULAR 为 Surge iOS 策略 | `CELLULAR + extended-matching` |
| [Coolapk.list](Services/Coolapk.list) | 酷安头像服务 | `DIRECT` |

### [Overrides/](Overrides) · 跨应用拦截例外

| 文件 | 用途 | 当前 Surge 策略 |
| --- | --- | --- |
| [Reject.list](Overrides/Reject.list) | 广告与追踪端点拦截 | `REJECT` |

### [Media/](Media) · 媒体服务规则

| 文件 | 用途 | 当前 Surge 策略 |
| --- | --- | --- |
| [JapanMedia.list](Media/JapanMedia.list) | 日本媒体图片与资源域名 | `🇯🇵日本智选` |
| [Adu](Media/Adu) | 成人媒体域名规则。工作配置使用 [vietnam 版](https://github.com/hht50/MyClashRules/blob/vietnam/Media/Adu) | `Yellow + no-resolve` |

### [Xiaomi/](Xiaomi) · 小米服务规则

| 文件 | 用途 | 当前 Surge 策略 |
| --- | --- | --- |
| [HyperConnect.list](Xiaomi/HyperConnect.list) | 小米互联服务的实测域名与 IP | `DIRECT` |

### [Meta/](Meta) · Meta 旗下及相关服务

| 文件 | 用途 |
| --- | --- |
| [Muse.list](Meta/Muse.list) | Muse 和 Meta AI 域名 |

Facebook、Instagram 等规则按产品归档在此目录。迁移已有规则时，先更新引用，再处理旧路径。注意 `meta.com` 是共用域名，使用不同策略时要核对 Surge 的匹配顺序。

## 引用和维护

- 在规则文件里只写匹配条件和必要注释。出站策略写在 Surge 的 `RULE-SET` 引用行。
- 迁移既有规则时，把引用放回原位置。Surge 按顺序采用首条命中的规则。
- 新域名优先用 `DOMAIN-SUFFIX`。仅限某个主机时用 `DOMAIN`，避免扩大匹配范围。
- `pre-matching` 写在拒绝策略的引用行。保留既有的 `no-resolve` 与 `extended-matching` 语义。
- `main` 和 `vietnam` 的 `Media/Adu` 内容分别维护。`sese.list` 是旧路径，供历史配置继续引用。
- 根目录旧规则和 `Stash/Overrides/` 沿用现有路径。变更文件名或位置前，先核对所有引用。

```ini
RULE-SET,https://raw.githubusercontent.com/hht50/MyClashRules/main/Services/115.list,DIRECT
```
