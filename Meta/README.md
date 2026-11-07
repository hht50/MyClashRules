# Meta 规则集

这个目录按产品维护 Meta 旗下及相关服务的域名规则。每个产品使用独立的规则文件，出站策略由引用它的 Surge 配置指定。

## 现有规则

| 文件 | 覆盖范围 |
| --- | --- |
| [Muse.list](Muse.list) | Muse 和 Meta AI 的 5 个域名后缀：`muse.ai`、`meta.ai`、`metaaivm.com`、`meta.com`、`metaaiusercontent.com` |

## 在 Surge 中引用

如果希望 Muse 走现有的 `Meta` 策略组，可以在 `[Rule]` 中加入：

```ini
RULE-SET,https://raw.githubusercontent.com/hht50/MyClashRules/main/Meta/Muse.list,Meta
```

`meta.com` 是共用域名。若 Muse 和其他 Meta 产品使用不同策略，先确认哪些请求应优先匹配。Surge 按顺序采用首条匹配的规则。

## 新增与迁移

- 文件按产品命名，例如 `Facebook.list`、`Instagram.list` 和 `Threads.list`。
- 规则文件只写匹配条件和注释。域名优先使用 `DOMAIN-SUFFIX`，需要限定单一主机时使用 `DOMAIN`。
- 迁移已有规则时，先发布新文件，再更新 Surge 引用。核对旧路径的使用情况后，再决定是否移除。
