## 1. Wallpapers 壁纸下载

Liunx Wallpapers 壁纸批量自动下载工具，默认下载目录为`/root/Pictures/Wallhaven`需先创建好目录

```bash
# 可指定存放位置，在指定位置执行命令
git clone https://github.com/touhidulshawan/waldl

# 进入waldl文件夹
cd waldl

# 安装pipenv
pip install pipenv

# 在waldl命令运行pipenv
pipenv install

# 激活虚拟命令
pipenv shell

# 执行应用
python waldl.py
```

## 2. 文件获取

### 1. 获取当前目录

使用`ls -R > filename1.txt`在当前目录中创建一个名为`filename1`的文件，其中包含当前目录及其下所有子目录的完整目录列表。

### 2. 获取指定目录

使用`ls -R /var > filename2.txt`获取`/var`，目录下所有文件及文件夹并在当前目录下创建`filename2.txt`文件

### 3. 获取文件树

在命令前加`find`获取文件目录树，比如`/www/1`下面有`name1`、`name2`，`name3`三个文件，执行`find /www/1 > filename3.txt`会列出`filename3.txt`会有：`/www/1/name1`、`/www/1/name2`、`/www/1/name3`三行数据。

### 4. 获取指定后缀文件

使用`find /dir -name "*.jpg" > filename4.txt`会获取到`/dir`目录下所有`*.jpg`文件

### 5. 更多参数


| 字段名 | 值 | 描述 |
| :----------: | :----------: | :----------: |
| -size | +/- | 按文件的大小查找文件，可用+为大于-为小于，k单位 |
| -atime | +/- | 按文件访问时间来查找文件，-n指n天以内，+n指n 天以前 | 
| -ctime | +/- | 按文件创建时间来查找文件，-n指n天以内，+n指n 天以前 | 
| -mtime | +/- | 按文件更改时间来查找文件，-n指n天以内，+n指n 天以前 | 
| -newer | file1 ! file2 | 查找更改时间比文件file1新但比文 件file2旧的文件 | 
| &#124 |  | 多参数使用 &#124 组合 |