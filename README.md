# xwork-updates

Xwork 的**升级分发仓**。本仓只放两类东西：

| 路径 | 作用 |
|---|---|
| `update/stable.json`、`update/beta.json` | 更新清单：最新版本号、包体积、sha256、增量包索引 |
| Release 附件 | 安装包本体：`Xwork-<版本>-win64.zip`、`delta-<旧>-to-<新>.zip`、`files-<版本>.json` |

**本仓不含任何源码。** 源码不在这个仓，也不在这个组织的公开仓库里；
客户端只把这里当作出包口，`https://raw.githubusercontent.com/gaio-x/xwork-updates/main/update/stable.json`
是更新检查读取清单的地址。

包体走 Release 附件而不是仓库树，是因为单包 170–220 MB，超过仓库单文件上限。

发布由 `tools/publish_update.py` 完成，写树前会过一遍硬白名单（只允许 `update/<channel>.json`），
事后由 `tools/guard_public_repo.py` 核对整仓，退出码非 0 即视为发布失败。
