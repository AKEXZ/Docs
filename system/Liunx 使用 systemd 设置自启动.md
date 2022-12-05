## 介绍

以Frp为例，创建系统自动启动文件

## 安装systemd

使用 yum 或 apt 等命令安装 systemd

```bash
# yum
yum install systemd
# apt
apt install systemd
```

使用vim，如果系统没vim使用`sudo apt-get install vim`安装，创建并编辑 `frpc.service` 文件

```bash
vim /etc/systemd/system/frpc.service
```

## 写入内容

```ini
[Unit]
Description = frpc server 
After = network.target syslog.target
Wants = network.target
 
[Service]
Type=simple
Restart=on-failure
RestartSec=5s
ExecStart = /root/Frp/frpc -c /root/Frp/frpc.ini
 
[Install]
WantedBy = multi-user.target

```


## 配置开机自启


依次执行p配置重载、开机启动

```bash
# 配置重载
systemctl daemon-reload

# 开机启动
systemctl enable frpc
```

## 管理命令

使用 `systemd` 命令，管理 frpc

```bash
# 启动frp
systemctl start frpc
# 停止frp
systemctl stop frpc
# 重启frp
systemctl restart frpc
# 查看frp状态
systemctl status frpc
```
