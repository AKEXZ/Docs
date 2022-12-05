# IOS玩机 - QuantumultX 基础配置使用教程

## 1. 介绍

Quantumult X 简称“圈X”，是一款功能强大的网络工具，本文主要介绍它的代理功能。是一款付费APP，7.99美元，需要用美区等AppleID账号登录 Apple Store 下载。Quantumult X 目前支持的功能：

- 支持shadowsocks代理协议。
- 支持带有obfs-tls或obfs-http插件的shadowsocks。
- 支持websocket和tls上的shadowsocks(服务器端应该由v2ray-core部署)。
- 如果服务器支持，则支持UDP中继。
- 通过使用自定义过滤器(主机、主机后缀、主机关键字)支持不同的网络请求策略...)
- HTTP activity可以记录整个HTTP请求和响应包括正文(HTTP debug应该启用)。 
- MitM HTTP解密可用于来自TUN接口的流量(应启用MitM)。 
- 使用URL 302/307重定向或请求标头/正文修改或响应标头/正文修改的HTTP重写(应启用重写)。 
- 特定域(IPv4或IPv6)的自定义DNS设置，只能在配置描述文件中编辑。

## 2. 懒人配置

- Tartarus2014`https://raw.githubusercontent.com/Tartarus2014/QuantumultX-Script/main/QuanX.conf`
- Orz-3`https://raw.githubusercontent.com/Orz-3/QuantumultX/master/Orz-3.conf`
- DivineEngine`https://raw.githubusercontent.com/DivineEngine/Profiles/master/Quantumult/Outbound.conf`
- KOP-XIAO`https://raw.githubusercontent.com/KOP-XIAO/QuantumultX/master/QuantumultX_Profiles.conf`
- Cuttlefish`https://ocd0522.tk/ddgksf2013/Cuttlefish/raw/branch/master/Profile/QuantumultX.conf`
- W37fhy`https://raw.githubusercontent.com/w37fhy/QuantumultX/master/QuantumultX_diy.conf`

### 添加懒人配置

打开QuantumultX，点击右下角小风车，选择右上角链接图标，在弹出的关联配置框内输入懒人配置链接，点击确定即可食用。

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1669288001-image-1669287999671.png?x-oss-process=style%2Ffull)

## 3. 分流配置

### (1). 分流规则是什么？

分流规则可以实现不同的网站走不同的节点，自动让网站或APP走指定的节点或策略组，不需要人工操作。

### (2). Quantumult X 分流规则类型

-   **HOST** / 域名匹配 / 例如：[www.google.com](http://www.google.com/)
-   **HOST-SUFFIX** / 域名后缀匹配 / 例如：google.com
-   **HOST-KEYWORD** / 域名关键字匹配 / 例如：google
-   **USER-AGENT** / 用户代理匹配 / 例如：*abc?
-   **IP-CIDR** / IP匹配 / 例如：192.168.0.1/24
-   **IP6-CIDR** / IPV6
-   **GEOIP** / IP数据库匹配 / 例如：US

### (3). 添加分流规则

分流规则（引用）示例：
- 回国`https://raw.githubusercontent.com/DivineEngine/Profiles/master/Quantumult/Filter/China.list`

打开QuantumultX，长按上方引用规则进入引用资源界面，点击右上方链接图标，自定义名称后输入分流配置地址。

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1669288039-image-1669288037615.png?x-oss-process=style%2Ffull)

## 4. 重写配置

### (1). 重写规则是什么

可以在页面中注入或修改一些信息。

### (2). 应用场景

1. 会员解锁
2. 广告屏蔽
3. 应用增强
4. 网页优化

### (2). 添加重写配置

打开QuantumultX，长按上方重写规则进入引用资源界面，点击右上方链接图标，自定义名称后输入重写配置地址。

重写规则（引用）示例：
- 京东比价`https://raw.githubusercontent.com/deezertidal/QuantumultX-Rewrite/master/rewrite/Price.conf`

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1669287967-image-1669287965535.png?x-oss-process=style%2Ffull)

## 5. 脚本配置

### (1). 脚本是什么

脚本像定时任务，跟iOS快捷指令类似，可进行每日签到、打卡等操作。

### (2). 添加脚本配置

打开QuantumultX，点击上方按钮进入脚本添加界面，点击右上方链接图标，自定义名称，根据推荐配置添加后输入重写配置地址。

 脚本规则（引用）示例：
- 疫情日报`https://raw.githubusercontent.com/Peng-YM/QuanX/master/Tasks/nCov.js`

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1669287826-image-1669287824114.png?x-oss-process=style%2Ffull)