## 一、 Debian

```bash
# 查看当前源
less /etc/apt/sources.list
```

内容如下：

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668252779-image-1668252777919.png?x-oss-process=style%2Ffull)

```bash
# 备份当前镜像源
cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

### 一键源

```bash
# 阿里源
sudo sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list
# 163源
sudo sed -i 's/deb.debian.org/mirrors.163.com/g' /etc/apt/sources.list
# 中科大源
sudo sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
# 清华源
sudo sed -i 's/deb.debian.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list
```

### 手动配置教程

```bash
# 修改当前镜像源，需要 root 权限
sudo vim /etc/apt/sources.list
```

打开文件不要做任何操作，直接输入 ggdG 清空文件，注意末尾 G 是大写，`ggdG`

以英文输入法按下`{i}`键，然后将下方相应版本的源粘贴进去，按下`{ESC}`键，输入`:wq`，保存退出

输入`sudo apt-get update`更新镜像源，等待输出完成

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668256386-image-1668256384424.png?x-oss-process=style%2Ffull)

大功告成，完成换源操作

### 1. 阿里源

```ini
deb http://mirrors.aliyun.com/debian/ stretch main
deb-src http://mirrors.aliyun.com/debian/ stretch main
deb http://mirrors.aliyun.com/debian-security stretch/updates main
deb-src http://mirrors.aliyun.com/debian-security stretch/updates main
deb http://mirrors.aliyun.com/debian/ stretch-updates main
deb-src http://mirrors.aliyun.com/debian/ stretch-updates main
```

### 2. 中科大源：

```ini
deb http://mirrors.ustc.edu.cn/debian/ stretch main
deb-src http://mirrors.ustc.edu.cn/debian/ stretch main
deb http://mirrors.ustc.edu.cn/debian-security stretch/updates main
deb-src http://mirrors.ustc.edu.cn/debian-security stretch/updates main
deb http://mirrors.ustc.edu.cn/debian/ stretch-updates main
deb-src http://mirrors.ustc.edu.cn/debian/ stretch-updates main
```

### 3. 163源

```ini
deb http://mirrors.163.com/debian/ stretch main
deb-src http://mirrors.163.com/debian/ stretch main
deb http://mirrors.163.com/debian-security stretch/updates main
deb-src http://mirrors.163.com/debian-security stretch/updates main
deb http://mirrors.163.com/debian/ stretch-updates main
deb-src http://mirrors.163.com/debian/ stretch-updates main
```

### 4. 清华源

```ini
deb http://mirrors.tuna.tsinghua.edu.cn/debian/ stretch main
deb-src http://mirrors.tuna.tsinghua.edu.cn/debian/ stretch main
deb http://mirrors.tuna.tsinghua.edu.cn/debian-security stretch/updates main
deb-src http://mirrors.tuna.tsinghua.edu.cn/debian-security stretch/updates main
deb http://mirrors.tuna.tsinghua.edu.cn/debian/ stretch-updates main
deb-src http://mirrors.tuna.tsinghua.edu.cn/debian/ stretch-updates main
```

## 二、 Contos

安装wget

```shell
yum install -y wget
```

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668257825-image-1668257824079.png?x-oss-process=style%2Ffull)

备份服务器原有的yum源文件

```bash
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
```

下载镜像文件，可根据对应Centos版本号更改链接

```bash
# 阿里源
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo

# 163源
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.163.com/.help/CentOS7-Base-163.repo

# 清华源
	# CentOS 7
sudo sed -e 's|^mirrorlist=|#mirrorlist=|g' \
         -e 's|^#baseurl=http://mirror.centos.org|baseurl=https://mirrors.tuna.tsinghua.edu.cn|g' \
         -i.bak \
         /etc/yum.repos.d/CentOS-*.repo
	# CentOS 8
sudo sed -e 's|^mirrorlist=|#mirrorlist=|g' \
         -e 's|^#baseurl=http://mirror.centos.org/$contentdir|baseurl=https://mirrors.tuna.tsinghua.edu.cn/centos|g' \
         -i.bak \
         /etc/yum.repos.d/CentOS-*.repo

# 中科大源
	# CentOS 7
sudo sed -e 's|^mirrorlist=|#mirrorlist=|g' \
         -e 's|^#baseurl=http://mirror.centos.org/centos|baseurl=https://mirrors.ustc.edu.cn/centos|g' \
         -i.bak \
         /etc/yum.repos.d/CentOS-Base.repo

	# CentOS 8
sudo sed -e 's|^mirrorlist=|#mirrorlist=|g' \
         -e 's|^#baseurl=http://mirror.centos.org/$contentdir|baseurl=https://mirrors.ustc.edu.cn/centos|g' \
         -i.bak \
         /etc/yum.repos.d/CentOS-Stream-AppStream.repo \
         /etc/yum.repos.d/CentOS-Stream-BaseOS.repo \
         /etc/yum.repos.d/CentOS-Stream-Extras.repo \
         /etc/yum.repos.d/CentOS-Stream-PowerTools.repo
```

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668258013-image-1668258012142.png?x-oss-process=style%2Ffull)

安装完成后执行命令

```bash
yum clean all #清理缓存
yum makecache #生成缓存
```

![file](https://cdn.memo.ak0.cn/wp-content/uploads/2022/11/1668258489-image-1668258487651.png?x-oss-process=style%2Ffull)

## 三、 Ubuntu

```bash
# 备份当前镜像源
cp /etc/apt/sources.list /etc/apt/sources.list.bak

# 阿里源
sudo sed -i 's/ru.archive.ubuntu.com/mirrors.aliyun.com/g' /etc/apt/sources.list
# 163源
sudo sed -i 's/ru.archive.ubuntu.com/mirrors.163.com/g' /etc/apt/sources.list
# 中科大源
sudo sed -i 's/ru.archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list
# 清华源
sudo sed -i 's/ru.archive.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list
```

安装完成后执行更新命令

```bash
sudo apt-get update
sudo apt-get upgrade
```
