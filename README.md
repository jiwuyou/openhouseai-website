# OpenHouse 平台官网

`https://openhouse.webefficacy.com` 的纯静态网站。

## 本地预览

```bash
python3 -m http.server 4174
```

网站不依赖构建工具。正式部署目录为 `mycloud:/var/www/openhouseai`，Nginx 站点为 `openhouse.webefficacy.com`。

OpenHouse Android 应用介绍位于 `https://app.webefficacy.com`，APK 下载服务位于 `https://app.stcplus.com`。

`/.well-known/openhouse-links.json` 是 OpenHouse 客户端使用的可扩展页面地址清单；同一份清单也部署在应用官网和 APK 下载服务上，作为回退解析源。
