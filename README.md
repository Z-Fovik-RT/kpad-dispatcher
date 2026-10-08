# kpad-dispatcher

KPad 优化调度 —— 在线更新用的仓库。

应用里的「检查更新」会读这里的 update.json，然后按里面的 url 下载新版 APK。

| 文件 | 用途 |
|---|---|
| update.json | 更新清单（版本号 / 大小 / SHA-256 / 更新说明） |
| KPad165.apk | 最新版安装包 |

update.json 由构建脚本自动生成，不要手工改。
手工抄 SHA-256 容易抄错，抄错会导致用户下载完校验不通过、装不上。

更新地址：

    https://raw.githubusercontent.com/Z-Fovik-RT/kpad-dispatcher/main/update.json