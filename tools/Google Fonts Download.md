# 谷歌字体下载分割版至本地 - 搭建本地谷歌字体 - Google Fonts Download

## 介绍

网站使用Google字体加速时，会有些无法加载字体的困扰，本教程使用CLI工具将分割后的谷歌字体下载至本地使用，通过提供网址可以使用此工具下载谷歌字体以供离线使用，只需提供谷歌API网址即可（因为谷歌字体总量庞大，所以只下载你站点需要的字体就行）。

## CLI工具:google-font-downloader

可下载woll2分割的格式字体，使用npm或yarn一键安装方便快捷。

请先确保服务器已经安装npm或者yarn环境。

```bash
# 用法 npm
npm install --global google-font-downloader # 实测暂无法使用，请使用yarn

# 用法 yarn
yarn global add google-font-downloader
```

### 执行

可以使用CLI工具运行`google-font-downloader --help`查看可执行的操作。

```dsconfig
# 用法:
google-font-downloader <链接> [配置]
# 通过提供网址下载谷歌字体
# 命令参数:
<url>  Google字体APIs链接.
# 选择:
-h, --help     # 显示帮助。
-v, --version  # 显示版本信息。
```

#### 举例

例如你需要谷歌的`Merriweather Sans`字体，在命令行输入下方代码，(名称空格字符请用+号代替)回车。

```bash
google-font-downloader https://fonts.googleapis.com/css?family=Merriweather+Sans:400,400i,700,700i
```

即可将字体下载至当前执行命令目录下的fonts 内。

CLI工具会自动生成css样式，存放在执行命令的当前目录下`google-fonts-<时间>.css`，需要自行修改css文件中的字体路径。

目录结构为`fonts/<字体名称>/<版本>/<字体文件>`。

## CLI工具:google-font-download

可下载FORMAT、eot、woff、woff2、svg、ttf，格式更多，支持更多自定义配置，但下载的不为分割后的格式，需在[GitHub](https://github.com/neverpanic/google-font-download/releases "GitHub")下载，将其解压后放置在合适目录，进入目录打开命令行。

### 配置

```dsconfig
    # 用法：google-font-download [OPTION...] [字体...]
    # 选择：

-u URL,--url=URL

    # 下载 URL 中指定的字体，可以将其与普通参数混合使用（见下文）

-f FORMAT,--format=FORMAT

    # 从谷歌的服务器下载指定的字体格式，需使用英文逗号分隔列表，支持的标识符有`,`和`.`。
    # 特殊值将按照1,2,3顺序下载所有支持的格式字体
    # 默认生成的css文件将按顺序包含字体格式浏览器会按顺序处理这些格式。
    # 注意可能不需要所有格式的文件，大多情况下WOFF和WOFF2就可以了。
    # 默认值为：'FORMA'，'Teo'，'twoff'，'woff2'，'svg'，'ttf'，'all'
    # 了解更多请参阅：http://caniuse.com/#search=woff

-h,--help

    # 使用帮助。

-l LANGSPEC,--languages=LANGSPEC

    #从谷歌的网络字体下载指定的语言， 需要使用逗号分隔列表，标识符为`,`。未设置的语言意味着提供完整文件。
    # 默认值为：'LANGSPEC'，'latin'，'latin-ext'，'cyrillic'，'cyrillic-ext'，'greek'，'greek-ext'，'all'。

-o OUTPUT,--output=OUTPU

    # 指定css文件名，如果文件存在将覆盖，否则将创建，默认为：`font.css`
```

### 使用

-   轻柔 (300),
-   正常 (400),
-   正常斜体 (400italic),
-   粗体 (700), and
-   粗斜体 (700italic):

```bash
google-font-download \
    "Open Sans:300" "Open Sans:400" "Open Sans:400italic" \
    "Open Sans:700" "Open Sans:700italic"
```

网址格式

```bash
google-font-download --url="https://fonts.googleapis.com/?selection.family=Open+Sans:300,400,400i,700,700i"
```

混合使用

```bash
google-font-download --url="https://fonts.googleapis.com/?selection.family=Open+Sans:300,400,400i" \
"Open Sans:700" "Open Sans:700i"
```

## 其他

如需使用第三方字体，推荐使用：[WebFont字体生成工具](https://transfonter.org/ "WebFont字体生成工具")，会自动生成css文件，合理搭配使用更香哦。

参考资料：[https://github.com/Bloggify/google-font-downloader/](https://github.com/Bloggify/google-font-downloader/)

参考资料：[https://github.com/neverpanic/google-font-download](https://github.com/neverpanic/google-font-download)