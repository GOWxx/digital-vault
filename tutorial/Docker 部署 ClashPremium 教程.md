# Docker 部署 ClashPremium

以下是 Docker 部署 ClashPremium 的步骤：

主要流程

- 一、安装 Docker
- 二、准备包含代理信息的 `config.yaml`
- 三、准备 Docker 需要的配置文件 `docker-compose.yaml`
- 四、准备 UI 界面
- 五、Docker 启动项目
- 六、外部控制界面访问，选择模式和节点
- 七、服务器内指向代理

**一、安装 Docker**

1. 首先，从 Docker Hub 上拉取 ClashPremium 镜像。可以通过以下命令拉取：
    
    ```bash
    docker pull dreamacro/clash-premium
    ```
    
2. 创建一个目录，用于保存配置文件和日志文件。可以通过以下命令创建一个名为 `clash` 的目录：
    
    ```bash
    mkdir clash
    cd clash
    ```
    

**二、准备包含代理信息的 `config.yaml`**

1. 从机场下载配置文件，命名成 `config.yaml` ，用于配置 ClashPremium。可以通过 FTP 上传到 clash 目录。
2. 编辑 `config.yaml` 文件，并按照自己的需要进行配置。以下是一个示例配置：
    
    ```yaml
    # 以下配置比较重要！
    port: 7890
    socks-port: 7891
    redir-port: 7892
    allow-lan: true
    mode: Rule
    log-level: info
    external-controller: 0.0.0.0:9090
    external-ui: /ui
    secret: "your secret"
    # 以上配置比较重要！
    # 以下配置是从机场获取的配置文件自带的，不用管。
    dns:
      enable: true
      listen: 0.0.0.0:53
      enhanced-mode: fake-ip
      fake-ip-range: 198.18.0.1/16
      nameserver:
        - 223.5.5.5
        - 223.6.6.6
    proxies:
      - name: "Proxy 1"
        type: ss
        server: "server ip"
        port: 8888
        cipher: "aes-256-gcm"
        password: "your password"
        udp: true
      - name: "Proxy 2"
        type: http
        server: "server ip"
        port: 8080
        username: "your username"
        password: "your password"
        tls: true
      - name: "Proxy 3"
        type: socks5
        server: "server ip"
        port: 1080
        username: "your username"
        password: "your password"
        udp: true
    
    ```
    
    着重看一下 `config.yaml` 配置文件中开头部分，这里我逐条解释下：
    
    ```yaml
    # 以下配置比较重要！
    # `port` 端口是主要设置的端口，在服务器内设置代理，指向的就是这个, 例如
    # export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
    port: 7890
    # `socks-port` 和 `redir-port` 端口跟着设置就行，不要和 `port` 相同，最好连续，比较方便设置
    socks-port: 7891
    redir-port: 7892
    # allow-lan 没什么影响，true 或 false
    allow-lan: true
    # 指的是全局模式还是规则模式，和前端界面的「代理页面」配合使用
    mode: Rule
    # 日志，不用改
    log-level: info
    # 外部控制端口
    external-controller: 0.0.0.0:9090
    # 前端界面路径
    external-ui: /ui
    # 前端界面访问的时候可以设置 secret，推荐设置！不然谁都可以访问你的控制页面
    secret: "your secret"
    # 以上配置比较重要！
    
    ```
    
    建议**要设置 secret！** 端口也可以改一改。
    

**三、准备 Docker 需要的配置文件 `docker-compose.yaml`**

1. 使用 `docker-compose` 部署 ClashPremium，创建一个名为 `docker-compose.yaml` 的文件，然后将以下内容复制到该文件中，放在 clash 目录内。
    
    ```yaml
    version: '3.8'
    services:
      clash:
        image: dreamacro/clash-premium
        container_name: clash-premium
        volumes:
          - ./config.yaml:/root/.config/clash/config.yaml
          - ./ui:/ui # 图形面板目录
        ports:
                - "7890:7890" # port 端口
                - "7891:7891" # socks-port 端口
                - "7892:7892" # redir-port 端口
                - "9090:9090" # 外部控制端口
        restart: unless-stopped
        network_mode: "bridge"
    
    ```
    

**四、准备 UI 界面**

1. 我们使用的是 https://github.com/haishanh/yacd ，下载代码、安装依赖、构建、把生成的 `public` 文件夹改名成 `ui`，发送到服务器 clash 目录内，与 `config.yaml` 和 `docker-compose.yaml` 同级。

```yaml
git clone https://github.com/haishanh/yacd.git
pnpm i
pnpm run build
```

**五、Docker 启动项目**

1. 现在 clash 目录内应该有 `ui` 文件夹、 `jian ui config.yaml` 、 `docker-compose.yaml`，执行以下命令启动容器：
    
    ```
    # 不同的 docker 版本启动命令可能不同，如果没能成功启动，查阅文档
    docker compose up -d
    
    ```
    
2. 现在 ClashPremium 已经成功部署了。可以通过浏览器访问 `http://服务器ip:7890/ui/` 来查看 Web UI。
3. 设置了 `secret` 的话记得在 optional 的位置输入密码，如果因为没有输入密码导致进入错误页面，浏览器清掉本页面 cookies 刷新即可。

另外，可以通过以下命令查看容器日志：

```bash
docker ps # 查看 id 和 name
docker logs id # 查看日志

```

**六、外部控制界面访问，选择模式和节点**

浏览器访问 `http://服务器ip:7890/ui/` 

有两种情况

如果本机没有开启 clash 服务，那么直接输入
ip:端口 和 密码 就可以

![Untitled](Untitled.png)

如果本机开启 clash 服务，那么很可能默认进入的是本机的控制界面，需要点击
配置 - switch to backend 到登陆界面
再输入服务器ip 端口 和 密码

![Untitled](Untitled%201.png)

进入控制界面，可以把 mode 改成 global, 再到代理界面选择合适的 global 节点。

**七、服务器内指向代理**

1. 指向代理

```bash
# 注意这里的端口要指向配置文件中设置的端口
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

1. 验证

用命令 `curl -I https://www.google.com` 验证，如果返回是 HTTP/1.1 200，说明代理配置生效。

```bash

[root@VM clash]# curl -I https://www.google.com
HTTP/1.1 200 Connection established

HTTP/2 200 
...
```

以上是 Docker 部署 ClashPremium 的全部流程，希望可以帮助到你。