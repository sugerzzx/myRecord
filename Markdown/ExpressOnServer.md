#在 linux 上安装 nodejs 环境并搭建 express 后端

##一：如何为 Debian 服务器配置 tls/ssl 加密？

为 Debian 服务器配置 TLS/SSL 加密是一项非常重要的任务，可以帮助保护 Web 应用程序免受数据泄露和 DDoS 攻击等攻击。本节将介绍如何为 Debian 服务器配置 TLS/SSL 加密。

首先，我们需要了解什么是 TLS 和 SSL。TLS（传输层安全性）和 SSL（安全套接字层）是一种广泛采用的安全性协议，旨在促进 Internet 上通信的隐私和数据安全性。TLS 和 SSL 的主要用例是对 Web 应用程序和服务器之间的通信进行加密。TLS 和 SSL 还可以用于加密其他通信，例如电子邮件，消息传递和 IP 语音（VOIP）。

然后，我们需要了解 TLS 的工作原理。TLS 连接使用称为 TLS 握手的序列启动。TLS 握手为每个通信会话建立一个密码套件。密码套件是一组算法，用于指定详细信息，例如哪些共享加密密钥或会话密钥将用于该特定会话。借助称为公钥加密的技术，TLS 能够通过未加密的通道设置匹配的会话密钥。握手还处理身份验证，通常包括服务器向客户端证明其身份。这是使用公钥完成的。公钥是使用单向加密的加密密钥，这意味着任何人都可以解密用私钥加密的数据以确保其真实性，但是只有原始发送者才能使用私钥加密数据。数据经过加密和身份验证后，便会使用消息身份验证代码（MAC）进行签名。接收者然后可以验证 MAC 以确保数据的完整性。

接下来，我们可以使用证书颁发机构（CA）来获取和安装免费 TLS / SSL 证书，从而在 Web 服务器上启用加密的 HTTPS。其中一个 CA 是 Let's Encrypt，它提供了一种获取和安装免费 TLS / SSL 证书的简便方法，通过提供软件客户端 Certbot 简化了流程，该客户端尝试自动化大多数（如果不是全部）所需步骤。目前，获取和安装证书的整个过程在 Apache 和 Nginx 上都是完全自动化的。许多 Debian 服务器使用 Nginx 作为 Web 服务器，因此我们可以使用 Certbot 来为 Debian 服务器配置 TLS / SSL 加密。

###具体步骤如下：

1. 安装 Certbot

   ```shell
   sudo apt-get update
   sudo apt-get install certbot python-certbot-nginx
   ```

2. 获取证书

   运行以下命令以获取证书：

   ```shell
   sudo certbot --nginx
   ```

   Certbot 将使用 Nginx 插件并自动配置 Nginx 以使用新证书。您将被提示输入您的电子邮件地址和同意条款。

3. 检查证书

   运行以下命令以检查证书是否已成功安装：

   ```shell
   sudo certbot certificates
   ```

   您应该看到您的证书详细信息。位置可能在`/etc/letsencrypt/live/example.com`路径

4. 配置 Nginx

   在您的 Nginx 配置文件中，

   ```shell
   /etc/nginx/nginx.conf
   ```

   确保以下行存在：

   ```shell
   listen 443 ssl;
   ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
   ssl_certificate_key /etc/letsencrypt/live/example.com/privkey.pem;
   ```

   具体位置是在 http 区块下的 server 区块

   ```shell
   http {
       server{
           listen 443 ssl;
           ssl_certificate /etc/letsencrypt/live/example.com/fullchain.pem;
           ssl_certificate_key /etc/letsencrypt/live/sexample.com/privkey.pem;
       }
       .......此处为其他配置项
   }
   ```

   其中 example.com 应替换为您的域名。保险起见，请先备份好该文件的初始版本。

5. 重新加载 Nginx

   运行以下命令以重新加载 Nginx：

   ```shell
   sudo systemctl reload nginx
   ```

   现在您的 Debian 服务器已经配置了 TLS/SSL 加密，您可以使用 HTTPS 访问您的 Web 应用程序。

6. 如果重载失败，输入以下命令查看原因

   ```shell
   sudo systemctl status nginx
   ```

   可能会看到如下信息，注意看第六行注释

   ```shell
   nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2023-05-07 01:46:30 UTC; 11min ago
       Docs: man:nginx(8)
   Process: 23587 ExecStartPre=/usr/sbin/nginx -t -q -g daemon on; master_process on; (code=exited, status=0/SUCCESS)
   Process: 23588 ExecStart=/usr/sbin/nginx -g daemon on; master_process on; (code=exited, status=0/SUCCESS) ///出现这个可能是因为nginx.conf配置有误，如果忘记了更改位置，使用备份好的初始文件替换当前文件
   Process: 28493 ExecReload=/usr/sbin/nginx -g daemon on; master_process on; -s reload (code=exited, status=1/FAILURE)
   Main PID: 23589 (nginx)
       Tasks: 2 (limit: 1149)
   Memory: 3.3M
   CGroup: /system.slice/nginx.service
           ├─23589 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
           └─23656 nginx: worker process

   May 07 01:46:30 vultr systemd[1]: Starting A high performance web server and a reverse proxy server...
   May 07 01:46:30 vultr systemd[1]: nginx.service: Failed to parse PID from file /run/nginx.pid: Invalid argument
   May 07 01:46:30 vultr systemd[1]: Started A high performance web server and a reverse proxy server.
   ```

7. 排查无误后，在浏览器输入`https://example.com`，如果能看到以下提示，证明你的服务器已经成功配置了 tls/ssl 加密

   ```shell
   Welcome to nginx!
   If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

   For online documentation and support please refer to nginx.org.
   Commercial support is available at nginx.com.

   Thank you for using nginx.
   ```

##二：安装 nodejs

######下列安装方式将会安装 Ubuntu 软件源中的 Node.js 版本。可能会导致 npm 不支持这些版本，安装最新版方式见下下文

为 Debian 安装 Node.js，您可以使用 apt 包管理器。请使用以下命令更新 apt 包列表，并安装 Node.js：

```shell
sudo apt update
sudo apt install nodejs
```

出现以下信息时

```shell
Do you want to continue? [Y/n] Y
```

输入 Y 回车或者直接回车（默认 Y）

您还可以安装 Node.js 命令行工具 npm，它将允许您管理和安装 Node.js 应用程序的依赖项。可以使用以下命令来安装 npm：

```shell
sudo apt install npm
```

请注意，使用 sudo 命令可以将特权提升到超级用户或管理员级别。安装 Node.js 和 npm 后，您可以使用以下命令检查它们的版本：

```shell
node -v
npm -v
```

####如何安装最新版：使用 NodeSource PPA 来安装更新的版本
使用以下命令添加 PPA

```shell
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
```

然后使用以下命令安装 Node.js：

```shell
sudo apt-get install -y nodejs
```

##三：搭建 Express 后端
在根目录新建一个工作区文件夹，在里面创建你的项目

1.  初始搭建

    在控制台输入命令，进入该路径

    ```shell
    cd /WorkStation/test    //WorkStation替换为你的工作区文件夹，test替换为你的项目文件夹
    ```

    输入命令

    ```shell
    npm init -y
    ```

    安装 express 库

    ```shell
    npm install experss
    ```

    新建一个 js 文件作为 app.js,编辑代码如下

    ```js
    const express = require("express");
    const app = express();
    const port = 3000;

    app.get("/test", (req, res) => res.send("Hello World!"));

    app.listen(port, () =>
      console.log(`MusicPlayerServer listening on port ${port}!`)
    );
    ```

    保存，控制台使用命令运行：

    ```shell
    node app.js
    ```

    控制台输出为
    `MusicPlayerServer listening on port 3000!`
    此时 express 服务端已经在工作并监听 3000 端口

2.  测试服务接口是否能访问

    1. 先用 postman 试一下：
       输入`https://sugerzzx.top:3000/test`,并 send 请求，返回结果为：

       ```
       Error: Client network socket disconnected before secure TLS connection was established
       // 意思是
        错误：客户端网络套接字在建立安全 TLS 连接之前断开连接
       ```

       产生这个错误的可能原因有:

       1. 网络连接不稳定,在传输过程中断开。这可能是临时网络问题,重试几次可解决。
       2. 防火墙或代理拦截了 TLS 握手的数据包,导致连接中断。需要检查防火墙规则并添加放行相关端口和域名。
       3. 证书问题,客户端无法验证服务器证书的有效性和权威性,导致 TLS 连接失败。需要检查证书链,更新或安装 CA 证书。
       4. TLS 协议版本不兼容,服务器要求使用较新版本的 TLS,而客户端不支持,导致连接中断。需要更新客户端或服务端支持的 TLS 版本。
       5. 其他网络异常,如 DNS 问题导致的错误域名解析等。需要检查整个连接过程,定位异常节点。

       其实不用猜就知道是防火墙的原因，需要在服务端的防火墙放行上面的 3000 端口

       先 Ctrl+C 停止 app.js,再在控制台输入放行命令

       ```shell
       ufw allow 3000/tcp
       ```

       使用命令检查防火墙状态

       ```shell
       ufw status
       ```

       输出为

       ```shell
       Status: active

           To                         Action      From
           --                         ------      ----
           22/tcp                     ALLOW       Anywhere
           443/tcp                    ALLOW       Anywhere
           80/tcp                     ALLOW       Anywhere
           3000/tcp                   ALLOW       Anywhere
           22/tcp (v6)                ALLOW       Anywhere (v6)
           443/tcp (v6)               ALLOW       Anywhere (v6)
           80/tcp (v6)                ALLOW       Anywhere (v6)
           3000/tcp (v6)              ALLOW       Anywhere (v6)
       ```

       看到 3000/tcp 已被放行

       再次用 postman 发送请求，可以看到输出为

       ```
       Error: write EPROTO 67763720:error:100000f7:SSL routines:OPENSSL_internal:WRONG_VERSION_NUMBER:../../../../src/third_party/boringssl/src/ssl/tls_record.cc:242:
       ```

       ~~查阅后得知这个错误提示说明在 SSL 握手过程中发生了错误，具体原因是服务器和客户端之间使用了不同的 SSL 协议版本。这通常意味着服务器使用了新版本的 SSL 协议，而客户端使用的是旧版本的 SSL 协议，无法正常通信。
       暂时找不到其他解决办法，最简单的解决办法时更换协议，使用 http，再次发送请求看到返回了`Hello World!`~~
       经过查阅，得知是 express 服务没有正确配置 SSL,导入 https 库，并添加以下代码

       ```js
       const https = require("https");
       const fs = require("fs");
       const sslOptions = {
         key: fs.readFileSync("key.pem"), //引号内替换你的证书密钥路径。如/etc/letsencrypt/live/example.com/key.pem
         cert: fs.readFileSync("cert.pem"), //同上，替换
       };

       const server = https.createServer(sslOptions, app);

       server.listen(3000, () => {
         console.log("Server listening on port 3000");
       });
       ```

       修改好的代码：

       ```js
           const express = require('express');
           const https = require('https');
           const cors = require("cors");
           const fs = require('fs');

           const app = express();
           app.use(cors());

           const port = 3000;
           const sslOptions = {
               key: fs.readFileSync('/etc/letsencrypt/live/example.com/privkey.pem'),
               cert: fs.readFileSync('/etc/letsencrypt/live/example.com/fullchain.pem')
           };
           const server = https.createServer(sslOptions, app);

           server.listen(3000, () => {
               console.log('Server listening on port 3000');
           });

           app.get('/test', (req, res) => {
               res.send('Hello World!);
           });
       ```

    2. 在浏览器上访问该接口：

       可以直接在地址栏输入`https://example.com:3000/test`

       也可以新建 html 文档，创建按钮点击事件发送请求：

       ```js
       const btn = document.querySelector("button");
       btn.addEventListener("click", () => {
         axios.get("https://sugerzzx.top:3000/test").then(res => {
           console.log(res.data);
         });
       });
       ```

       返回结果：

       ```shell
       Access to XMLHttpRequest at 'http://sugerzzx.top:3000/test' from origin 'http://127.0.0.1:5500' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
       ```

       这是由于浏览器无法访问 http://sugerzzx.top:3000/test 这个跨域 URL,因为该服务端没有返回 Access-Control-Allow-Origin 头。

       导入 cors 库`npm install cors`重新编辑 app.js,加入以下代码：

       ```js
       const cors = require("cors");
       app.use(cors());
       ```

       这样浏览器客户端就能请求到该接口了，返回了`Hello World!`

##四：安装 和使用 mongodb

1. 安装：
   在 Debian 上，MongoDB 已经包含在软件包存储库中。但是，为了获得最新版本，我们可以使用官方 MongoDB 存储库。在这一步中，我们需要导入官方 MongoDB 存储库的密钥，并添加存储库详细信息，以便 apt 知道从哪里下载软件包。

   - 添加 MongoDB GPG 密钥：

   ```shell
   wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
   ```

   - 添加 MongoDB 存储库：

   ```shell
   echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/debian $(lsb_release -cs)/mongodb-org/5.0 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
   ```

   - 更新 apt 软件包列表：

   ```shell
   sudo apt update
   ```

   - 安装 MongoDB：

   ```shell
   sudo apt install mongodb-org
   ```

   - 启动 MongoDB 服务

   ```shell
       sudo systemctl start mongod
   ```

   - 使用 systemctl 检查服务是否已正确启动：

   ```shell
   sudo systemctl status mongod
   ```

   出现`Active: active (running) since Sun 2023-05-07 05:56:07 UTC; 5s ago`字样表明服务正在运行

2. 使用
   - mongoDB shell ：
     控制台输入`mongo`，随后输入`show dbs`可以看见数据库信息：
   ```shell
      admin   0.000GB
      config  0.000GB
      local   0.000GB
   ```
   - 使用 mongoDB Compass 进行远程连接

# 待续，不好搞
