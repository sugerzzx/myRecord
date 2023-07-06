# 什么是 Nginx?

Nginx 是一个高性能的 HTTP 和反向代理服务器，也是一个 IMAP/POP3/SMTP 服务器。有了 Nginx，你便可以在一台服务器上运行多个 Web 应用，而每个 Web 应用都监听于不同的端口，Nginx 服务器则负责根据用户的访问域名，将请求反向代理到相应的 Web 应用上。

# 使用 Nginx 部署你的第一个静态网站

## 1. 安装及 SSL 证书配置见[ExpressOnServer](./ExpressOnServer.md)

## 2. 上传你的静态网站

在我们初次配置好 Nginx 时，访问域名便能看到一个来自 Nginx 官方的欢迎页面，这是因为 Nginx 配置默认的静态文件目录是`/var/www/html`，我们只需要将我们的静态网站上传到这个目录下即可。

你也可以去 `/etc/nginx/sites-available/default` 中修改默认的静态文件目录。

```
# ...
root /var/www/html; # 修改这里的路径
# ...
```

修改之后，重启 Nginx 服务即可。

```bash
sudo service nginx restart
```

这时，当你访问域名时，便能看到你的静态网站了。

## 3. 配置 Nginx 反向代理

...
