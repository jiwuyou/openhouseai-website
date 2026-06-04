# openhouse ai 官网

这是 openhouse ai 的官网静态站仓库。

## 本地预览

不需要安装依赖，可以直接启动一个静态文件服务器：

```bash
python3 -m http.server 4174
```

然后访问：

```text
http://127.0.0.1:4174
```

## 自动部署

仓库内置 GitHub Actions workflow：`.github/workflows/deploy.yml`。

需要在 GitHub 仓库 Settings -> Secrets and variables -> Actions 中配置：

```text
DEPLOY_HOST       服务器 IP 或域名
DEPLOY_USER       SSH 用户名
DEPLOY_KEY        SSH 私钥
DEPLOY_PATH       部署目录，例如 /var/www/openhouseai
```

服务器建议使用 Nginx 指向 `DEPLOY_PATH`。

示例 Nginx 配置：

```nginx
server {
    listen 80;
    server_name example.com;

    root /var/www/openhouseai;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

## 部署流程

推送到 `main` 分支后，GitHub Actions 会通过 SSH 将仓库文件同步到服务器：

```text
git push origin main
```
