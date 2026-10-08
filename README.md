# kpad-dispatcher

KPad 优化调度 —— 在线更新用的仓库。

应用里的「检查更新」会读这里的 `update.json`，然后按里面的 `url` 下载新版 APK。

| 文件 | 用途 |
|---|---|
| `update.json` | 更新清单（版本号 / 大小 / SHA-256 / 更新说明） |
| `kpad-dispatcher-x.y.apk` | 最新版安装包（文件名带版本号） |

更新地址：

    https://raw.githubusercontent.com/Z-Fovik-RT/kpad-dispatcher/main/update.json

## 为什么 APK 文件名带版本号

不要改成固定文件名。GitHub raw 的 CDN 会缓存几分钟，而且是**忽略查询参数**地缓存 ——
覆盖上传同名文件后，用户可能拿到「新清单 + 旧 APK」，应用会报「SHA-256 校验不通过」。
文件名带版本号后，每次发版都是全新 URL，缓存问题就不存在了。

## 别手工改 update.json

它由构建脚本自动生成（版本号、大小、SHA-256 都从真实 APK 上算出来）。
手工抄 SHA-256 容易抄错，抄错会导致用户下载完校验不通过、装不上。

发版走 `release.ps1`：构建 → 校验 → 同步到这个仓库 → 推送，一条命令。
