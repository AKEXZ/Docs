## 介绍

V2Ray 是一个于 Shadowsocks 之后非常好用的代理软件，但是由于 V2Ray 的配置略复杂，GUI 客户端不完善，所以 V2Ray 并没有像 Shadowsocks 在科学上网人群之中那么流行。不过我想，像我这种小小白萌新，更需要的是一个好用的一键安装脚本……所以，此脚本是为了方便像我这种小小白萌新更加容易去使用 V2Ray，配置 V2Ray。希望对你有帮助 ^\_^

## 一、V2Ray 一键安装/管理脚本 By 233v2

### 1\. 脚本功能特点

+   一键脚本功能特点协议
+   支持 V2Ray 多数传输协议
+   支持 WebSocket + TLS / HTTP/2
+   支持 动态端口 (WebSocket + TLS，Socks5， HTTP/2 除外)
+   支持 屏蔽广告
+   支持 配置 Shadowsocks
+   支持 下载客户端配置文件 (不用 Xshell 也可以下载)
+   客户端配置文件同时支持 SOCKS 和 HTTP
+   支持 生成 V2Ray 配置二维码链接 (仅适用部分客户端)
+   支持 生成 V2Ray 配置信息链接
+   支持 生成 Shadowsocks 配置二维码链接
+   支持修改 V2Ray 传输协议
+   支持修改 V2Ray 端口
+   支持修改 动态端口
+   支持修改 用户ID
+   支持修改 TLS 域名
+   支持修改 Shadowsocks 端口
+   支持修改 Shadowsocks 密码
+   支持修改 Shadowsocks 加密协议
+   自动启用 BBR 优化 (如果内核支持)
+   集成可选安装 BBR (by teddysun.com)
+   集成可选安装 锐速 (by moeclub.org)
+   一键 查看运行状态 / 查看配置信息 / 启动 / 停止 / 重启 / 更新 / 卸载 / 等等…
+   人性化向导 & 纯净安装 & 卸载彻底

### 2\. 安装Curl依赖包

```bash
# Ubuntu/Debian
apt-get update -y && apt-get install curl -y
```

```bash
# CentOS
yum update -y && yum install curl -y
```

### 3\. 安装V2Ray一键安装脚本，执行命令如下：

```shell
bash <(curl -s -L https://git.io/v2ray.sh)
```

安装完成后，输入命令：v2ray，即可进行管理。

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668244391-image-1668244389945.png?x-oss-process=style%2Ffull)

**温馨提醒：**如果你是小白用户，遇到每次提示要你选择或属于的时候，你直接一直按Enter键就可以了，默认是开启TCP协议的V2Ray，而且中转速度挺不错。如果你是 CentOS/Fedora 系统，那么用233boy大神的一键安装脚本搭建V2Ray服务器时，你需要手动放行服务器端口，否则无法正常科学上网。相关命令如下：

```bash
# 查看已放行的端口：
firewall-cmd --list-ports
# 放行服务器端口：
firewall-cmd --zone=public --add-port=1688/tcp --permanent
# 关闭服务器端口：
firewall-cmd --zone=public --remove-port=1688/tcp --permanent
# 重启防火墙：
firewall-cmd --reload
```

**注意事项：**以上1688必须换成你自己的服务器端口号，tcp换成你正在使用的协议，放行服务器端口后，必须重启防火墙才能生效。

233一键脚本安装V2Ray传输协议选项，如下图所示：

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668244222-image-1668244220138.png?x-oss-process=style%2Ffull)

233一键脚本安装配置Shadowsocks信息，如下图所示：

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668244238-image-1668244236823.png?x-oss-process=style%2Ffull)

233一键脚本安装完成后V2Ray配置信息，如下图所示：

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668244250-image-1668244248592.png?x-oss-process=style%2Ffull)

### 4\. V2Ray快速管理命令：

```bash
v2ray info #查看 V2Ray 配置信息  
v2ray config #修改 V2Ray 配置  
v2ray link #生成 V2Ray 配置文件链接  
v2ray infolink #生成 V2Ray 配置信息链接  
v2ray qr #生成 V2Ray 配置二维码链接  
v2ray ss #修改 Shadowsocks 配置  
v2ray ssinfo #查看 Shadowsocks 配置信息  
v2ray ssqr #生成 Shadowsocks 配置二维码链接  
v2ray status #查看 V2Ray 运行状态  
v2ray start #启动 V2Ray  
v2ray stop #停止 V2Ray  
v2ray restart #重启 V2Ray  
v2ray log #查看 V2Ray 运行日志  
v2ray update #更新 V2Ray  
v2ray update.sh #更新 V2Ray 管理脚本  
v2ray uninstall #卸载 V2Ray
```

### 5\. 配置文件路径

V2Ray 配置文件路径：`/etc/v2ray/config.json` Caddy 配置文件路径：`/etc/caddy/Caddyfile` 脚本配置文件路径: `/etc/v2ray/233blog\_v2ray\_backup.conf`

### 6\. WS+TLS / HTTP2 配置

如果你使用了这两个协议，那么就会使用了脚本自带的 Caddy 集成。不管如何，不建议直接去更改 Caddy 的配置：/etc/caddy/Caddyfile；如果你需要配置其他网站，请将网站的配置文件放到/etc/caddy/sites目录下，然后重启 Caddy 进程即可，脚本默认生成的 Caddy 的配置会加载 /etc/caddy/sites 这个目录下的所有配置文件。所以，请将你的网站配置文件放到/etc/caddy/sites目录下，完完全全不需要去更改/etc/caddy/Caddyfile，然后一定要重启 Caddy 进程，执行如下命令：

```shell
service caddy restart
```

### 7\. Caddy 插件相关

V2Ray 一键安装脚本 & 管理脚本 By 233v2.com 集成了 Caddy，但不集成任何 Caddy 插件，如果你需要安装某些 Caddy 插件，你可以使用官方的 Caddy 安装脚本来一键安装。本脚本集成的 Caddy 的安装路径，跟 Caddy 官方的安装脚本是一致的，可直接安装，不会有任何问题。

## 二、 multi-v2ray 多用户管理脚本

### 1\. 介绍

multi-v2ray 是 V2ray 多用户管理脚本，向导式管理\[新增|删除|修改\]传输协议，功能非常强大，让您享受使用V2ray科学上网的乐趣~

### 2\. 功能特色

+   命令行模式管理v2ray，支持程序和命令行参数管理控制；
+   流量统计(v2ray && iptables)，调用v2ray官方api进行流量统计；
+   支持多用户、单端口和多端口修改管理，支持混合传输协议管理；
+   首次安装时产生随机端口，默认配置mkcp + 随机一种 (srtp | wechat-video | utp | dtls | wireguard) header伪装，安装完成显示配置信息;
+   查看配置信息显示vmess字符串(v2rayN的分享链接格式)；
+   生成Telegram的socks5/MTProto分享链接, 支持socks5 + tls组合；
+   支持http/2, 随机生成伪装h2 path；
+   开启关闭tcpFastOpen；
+   直接开启CDN，直接走Cloudcflare CDN；
+   开启关闭动态端口；
+   一键 启动 / 停止 / 重启 V2ray 服务端；
+   快速查看服务器连接信息, 常规配置修改；
+   定时更新v2ray(需手动开启)；
+   支持新版v2ray配置文件格式(v4.1+)；
+   支持docker部署；
+   支持纯IPV6 VPS；
+   支持开启或禁止BT下载。

### 3\. 自定义传输方式

+   常规TCP
+   HTTP头部伪装
+   WebSocket流量
+   常规mKCP流量
+   mKCP 伪装 FaceTime通话流量(srtp)
+   mKCP 伪装 BT下载流量(utp)
+   mKCP 伪装 微信视频通话流量(wechat-video)
+   mKCP 伪装 DTLS 1.2流量(dtls)
+   mKCP 伪装 WireGuard流量(wireguard)
+   HTTP/2的tls流量(h2)(需备域名)
+   Socks5
+   MTProto
+   Shadowsocks
+   Quic

### 4\. 安装Curl依赖包

```bash
# Ubuntu/Debian
apt-get update -y && apt-get install curl -y
# CentOS
yum update -y && yum install curl -y
```

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668507212-image-1668507210857.png?x-oss-process=style%2Ffull)

### 5\. 安装/升级/卸载

```bash
# 一键安装命令
source <(curl -sL https://multi.netlify.app/v2ray.sh) --zh
# 升级命令(保留配置文件更新)
source <(curl -sL https://multi.netlify.app/v2ray.sh) -k
# 卸载命令
source <(curl -sL https://multi.netlify.app/v2ray.sh) --remove
```

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668507396-image-1668507394928.png?x-oss-process=style%2Ffull)

### 6\. V2Ray管理命令行参数

```bash
v2ray [-h|--help] [options]
    -h, --help           查看帮助
    -v, --version        查看版本号
    start                启动 V2Ray
    stop                 停止 V2Ray
    restart              重启 V2Ray
    status               查看 V2Ray 运行状态
    new                  重建新的v2ray json配置文件
    update               更新 V2Ray 到最新Release版本
    update.sh            更新 multi-v2ray 到最新版本
    add                  新增mkcp + 随机一种 (srtp|wechat-video|utp|dtls|wireguard) header伪装的端口(Group)
    add [wechat|utp|srtp|dtls|wireguard|socks|mtproto|ss]     新增一种协议的组，端口随机,如 v2ray add utp 为新增utp协议
    del                  删除端口组
    info                 查看配置
    port                 修改端口
    tls                  修改tls
    tfo                  修改tcpFastOpen
    stream               修改传输协议
    cdn                  走cdn
    stats                v2ray流量统计
    iptables             iptables流量统计
    clean                清理日志
    log                  查看日志
```

## 三、 v2-ui安装 Xray 可视化面板

### 1\. 介绍

v2-ui 是一款非常出名的支持多协议多用户的 V2Ray 面板，是非常优秀的V2Ray一键多用户多协议安装与管理脚本，由原 sprov-ui 的作者sprov使用 Python 语言重新开发而成。

### 2\. 功能

+   系统状态监控
+   支持多用户多协议，浏览器可视化操作，无需敲命令
+   支持的协议：vmess、shadowsocks、dokodemo-door、socks、http
+   vmess 支持的传输配置：tcp（http伪装、tls）、kcp（伪装）、ws（tls）、http（tls）、quic（tls）
+   支持账号流量统计
+   支持自定义 v2ray 配置模板
+   支持 https 访问面板（需自备域名 + ssl 证书）
+   更多高级配置项，详见面板

v2-ui 支持CentOS 7、Ubuntu 16、Debian 8及以上版本的64位系统，作何建议使用最新版。

### 3\. 安装

安装依赖包，执行如下命令：

```bash
# CentOS/Fedora
yum install curl -y
# Debian/Ubuntun
apt-get update && apt-get install sudo curl -y && sudo -i
```

v2-ui 一键安装脚本，执行代码如下：

```bash
# 官方源
bash <(curl –Ls https://blog.sprov.xyz/v2-ui.sh) #实测无法使用
# Github源
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668509065-image-1668509063840.png?x-oss-process=style%2Ffull)

### 4\. 注意

安装后访问`IP:65432`进入UI面板默认账号密码：admin，v2-ui 与其它所有关于修改 v2ray 配置文件的工具完全不兼容（包括 sprov-ui），安装 v2-ui 后会导致 v2ray 配置文件被重写，导致原有 v2ray 账号丢失，如有必要，请自行提前做好备份，以免造成不必要的后果。若之前安装过非官方的 v2ray，建议先卸载，否则可能会造成冲突。

### 5\. 常用命令

```bash
- v2–ui # 显示管理菜单 (功能更多)
- v2–ui start # 启动 v2-ui 面板
- v2–ui stop # 停止 v2-ui 面板
- v2–ui restart # 重启 v2-ui 面板
- v2–ui status # 查看 v2-ui 状态
- v2–ui enable # 设置 v2-ui 开机自启
- v2–ui disable # 取消 v2-ui 开机自启
- v2–ui log # 查看 v2-ui 日志
- v2–ui update # 更新 v2-ui 面板
- v2–ui install # 安装 v2-ui 面板
- v2–ui uninstall # 卸载 v2-ui 面板
```

在 VPS 输入 `v2-ui restart` 对面板和 Xray 进行重启，使得配置生效

## 四、V2Ray 基于 Nginx 的 vmess+ws+tls 一键安装脚本

### 1\. 介绍

此脚本由 wulabing 大神创作的单用户V2Ray一键脚本，目前支持Debian 9+ / Ubuntu 18.04+ / Centos7+系统，包含“Vmess+websocket+TLS+Nginx+Website”和“Vmess+https2+TLS+Nginx+Website”2种V2Ray模式，安装其中1种即可，一般推荐安装“Nginx+ws+tls”模式。

### 2\. 功能

+   新增 交互式菜单，重构为安装管理脚本，版本号初始化为 1.0，诸多功能合并；
+   合并 h2 版合并至主版本并跟随更新，h2 版（旧版）停止维护；
+   新增 变更 UUID ALTERID PORT TLS 版本选项；
+   新增 V2ray 日志记录及查看；
+   新增 4 合 1 bbr 锐速脚本引入，感谢 94ish.me；
+   新增 卸载选项；
+   新增 let’s encrypted 证书手动更新，原理与计划任务更新相同，证书有效期仅小于 30 天可更新，默认不启用强制更新，理论上自动生成的证书支持自动续签。

安装依赖包，执行如下命令：

```bash
# CentOS/Fedora
yum -y install wget
yum update -y && yum install curl -y
# Debian/Ubuntun
apt-get install wget
apt-get update -y && apt-get install curl -y
```

### 3\. 一键脚本

```bash
wget -N --no-check-certificate -q -O install.sh "https://raw.githubusercontent.com/wulabing/V2Ray_ws-tls_bash_onekey/master/install.sh" && chmod +x install.sh && bash install.sh
```

### 4\. 相关命令

```bash
# 启动 V2ray
systemctl start v2ray
# 停止 V2ray
systemctl stop v2ray
# 启动 Nginx
systemctl start nginx
# 停止 Nginx
systemctl stop nginx
```

### 5\. 相关目录

伪装的 Web 目录：`/home/wwwroot/3DCEList` V2ray 服务端配置：`/etc/v2ray/config.json` V2ray 客户端配置: 执行安装时所在目录下的 `v2ray_info.txt` Nginx 目录： `/etc/nginx` 证书文件: `/data/v2ray.key` 和 `/data/v2ray.crt`

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668509414-image-1668509412861.png?x-oss-process=style%2Ffull)

## 必装软件BBR

[\[一键开启BBR加速 - 搭建CDN防被墙\]](https://memo.ak0.cn/159 "一键开启BBR加速 - 搭建CDN防被墙")