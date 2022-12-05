## 介绍

frp 是一个专注于内网穿透的高性能的反向代理应用，支持 TCP、UDP、HTTP、HTTPS 等多种协议。可以将内网服务以安全、便捷的方式通过具有公网 IP 节点的中转暴露到公网。 

---

通过在具有公网 IP 的节点上部署 frp 服务端，可以轻松地将内网服务穿透到公网，同时提供诸多专业的功能特性，这包括：

-   客户端服务端通信支持 TCP、KCP 以及 Websocket 等多种协议。
-   采用 TCP 连接流式复用，在单个连接间承载更多请求，节省连接建立时间。
-   代理组间的负载均衡。 端口复用，多个服务通过同一个服务端端口暴露。
-   多个原生支持的客户端插件（静态文件查看，HTTP、SOCK5 代理等），便于独立使用 frp 客户端完成某些工作。
-   高度扩展性的服务端插件系统，方便结合自身需求进行功能扩展。
-   服务端和客户端 UI 页面。

---

## Frp服务端

### 服务端一键安装/更新/卸载指令

#### Aliyun 目前无法使用，等待作者更新

```bash
~~wget https://code.aliyun.com/MvsCode/frps-onekey/raw/master/install-frps.sh -O ./install-frps.sh
chmod 700 ./install-frps.sh
./install-frps.sh install~~
```

#### Github

```bash
wget https://raw.githubusercontent.com/MvsCode/frp-onekey/master/install-frps.sh -O ./install-frps.sh
chmod 700 ./install-frps.sh
./install-frps.sh install
```

#### 其他指令

```bash
./install-frps.sh uninstall #卸载
./install-frps.sh update    #更新

```

#### 详细步骤

执行一键安装命令，如无特殊需要只需要一路回车即可，其他科根据需求进行修改。

![内网穿透之Frp搭建](https://cdn.memo.ak0.cn/wp-content/uploads/2022/10/1666260672-image-1666260672016.png?x-oss-process=style%2Ffull "内网穿透之Frp搭建")

如需访问网页后台需要设置`dashboard_user与dashboard_pwd`，搭建完成后访问`IP:dashboard_port`输入账号密码登录网页后台即可。

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/10/1666261183-image-1666261183205.png?x-oss-process=style%2Ffull)

安装完成的配置如下

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/10/1666261357-image-1666261356590.png?x-oss-process=style%2Ffull)

服务端默认配置即可，使用回车进行安装，安装完成后去需要穿透的内网电脑上安装Frpc客户端。[warning]如果下载frp时失败请使用下方手动安装教程再试[/warning]

### 手动安装

#### 介绍

因aliyun目前无法使用，可以手动安装在国内无法连接Github的服务器。

#### 配置

可以先使用[Github](https://memo.ak0.cn/wp-admin/post.php?post=1&action=edit&classic-editor#Github "Github")的命令生成frps.ini的配置

到这一命令后直接`ctrl`+`c`退出安装，因为接下来的命令是下载frps和执置，这里因为无法下载所以直接取消，进行手动下载安装

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/10/1668826551-image-1668826536038.png?x-oss-process=style%2Ffull)

#### 下载

进入[https://github.com/fatedier/frp/releases](https://github.com/fatedier/frp/releases) 根据对应系统下载相应文件，这里我下载的frp_0.45.0_freebsd_386.tar.gz，下载后解压，将文件夹内的frps文件上传至`/usr/local/frps`目录下，文件需要执行权限，将文件权限设置为`755`，目录下原有的`frps.ini`文件**不要更改、不要替换**，是你刚才使用一键安装指令创建的配置文件，

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/10/1668828939-image-1668828938420.png?x-oss-process=style%2Ffull)

进入[https://raw.githubusercontent.com/MvsCode/frps-onekey/master/frps.init](https://raw.githubusercontent.com/MvsCode/frps-onekey/master/frps.init) 将该页面保存为frpc文件，**注意不要带后缀**，将文件上传至服务器`/etc/init.d`目录与`/usr/bin`下，文件需要执行权限，请将文件权限设置为`755`，执行命令`update-rc.d -f frps defaults`命令，如果你的系统是CentOS/Redhat 需要再运行`chkconfig --add frps`。

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/10/1668833821-image-1668833813102.png?x-oss-process=style%2Ffull)

## Frp客户端

前往Github下载最新版本。

### 安装

将下载的文件夹解压，frpc为客户端文件，frps为服务器端文件。 ![内网穿透之Frp搭建](https://cdn.memo.ak0.cn/wp-content/uploads/2022/10/1666257266-1666171574-image-1666171574811.png?x-oss-process=style%2Ffull "内网穿透之Frp搭建")

在root文件夹内新增Frp文件夹，将frpc与frpc.ini文件放于新建的Frp文件夹内并配置ini文件。

![内网穿透之Frp搭建](https://cdn.memo.ak0.cn/wp-content/uploads/2022/10/1666257296-1666172096-image-1666172096843.png?x-oss-process=style%2Ffull "内网穿透之Frp搭建")

#### Liunx启动

配置完ini文件后使用 `./Frp/frpc -c ./Frp/frpc.ini` 启动Frp服务

#### 配置ini

frpc_full.ini是官方提供的参考,这里我提供一个我在用的模板

#### 模板

```ini
[common]
server_addr = 45.128.222.17 #服务器IP
server_port = 5443  #搭建frps服务端时的填写的端口
token = 123456789   #搭建frps服务端时自动生成的token
server_port = 7000  #通过SSH访问内网机器（该端口为外网公开访问内网SSH的端口，如需使用请在外网配置[common]下加入bind_port = 7000）

[web_memo_http] #http可以自定义名称，如需开通80与443端口可根据内容自行修改，注意开通https需要设置网站证书。type = httplocal_port = 80custom_domains = memo.ak0.cn
[web_memo_https]type = httpslocal_port = 443custom_domains = memo.ak0.cn
证书相关配置 （由于我使用的为宝塔搭建的站点，所以添加的是宝塔证书的路径，可根据实际情况自行修改证书地址）
```

#### 高级自定义

可前往[Frp官方文档](https://gofrp.org/docs/ "Frp官方文档")查看教程，这里不予详细说明

## 其他

### 参考资料

[Frps-Onekey](https://github.com/MvsCode/frps-onekey "Frps-Onekey")一键搭建服务端脚本进行搭建 [Frp官方文档](https://gofrp.org/docs/ "Frp官方文档")自行配置客户端

