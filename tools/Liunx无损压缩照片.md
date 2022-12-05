# Liunx使用命令批量格式转换 - 无损压缩照片

## 1. 介绍

通过过`OptiPNG`和`jpegoptim`工具来对图片进行压缩。

**jpegoptim：** 一个优化/压缩JPEG文件而不降低其质量的工具，可将图片压缩图片至指定大小，比如把某图片大小压缩到100k大小，但这是要损失图片质量的，支持的照片格式有：`.jpg`/`.jpeg`。

**OptiPNG：** 一个命令行工具，用于优化和压缩PNG(可移植网络图形)文件，而不丢失其原始质量，支持的照片格式有：`.bmp`/`.png`。

~~**imagemagick：** 一个很高效的命令行图片处理工具，它可以对超过 100 种的图像格式（包括 `DPX`, `EXR`, `GIF`, `JPEG`, `JPEG-2000`, `PDF`, `PhotoCD`, `PNG`, `Postscript`, `SVG`, 和 `TIFF`等等），进行读、写、编辑、压缩和转换的操作。~~ 待添加

## 2. 安装环境

```bash
# Debian/Ubuntu
## 安装jpegoptim
sudo apt-get install jpegoptim
## 安装optipng
sudo apt-get install optipng
## 安装ImageMagick


# CentOS/Redhat
## 安装epel源 
yum install epel-release 
## 安装OptiPNG 
yum install optipng 
## 安装jpegoptim 
yum install jpegoptim
```

## 3. 使用

### 1. jpegoptim

#### 1. 基础命令

只能压缩`jpg`、`jpeg`类型，无损压缩率超低，3%左右

```bash
# 默认指令，默认情况只进行无损压缩
jpegoptim tupian.jpeg

# 指定照片大小（损失质量）
jpegoptim --size=100k tupian.jpeg

# 批量文件大于500k的图片压缩
 find 路径 -name '*.jpg' -size +500 | xargs jpegoptim
```

#### 2. 其他参数

```config
名称
	jpegoptim - 用于优化/压缩JPEG/JFIF文件。
概要
    jpegoptim [ options ] [ filenames ]
描述
    pegoptim用于优化/压缩jpeg文件。项目支持无损优化，这是基于对Huffman表的优化。所谓的“有损”优化除了优化之外。可以指定图像质量的上限。
选项
    选项可以是传统的POSIX一个字母选项，也可以是。GNU风格长选项。 POSIX风格选项以一个“-”开头，而GNU的长选项以''--'开头。
       
options:
       
	-d<path>, --dest=<path>
	//设置备选目标目录，以便保存优化。文件(默认是覆盖原始文件)。
	//请注意,不变的文件不会被添加到目标目录。
	//这意味着如果源文件不能被压缩，就不会有文件。在目标路径中创建。
	
	-f, --force
	//强制优化，即使结果大于。原始文件。
	
	-h, --help
	//显示简短的使用信息并退出。
	
	-m<quality>, --max=<quality>
	//设置最大图像质量因子(禁用无损优化)。mization模式是默认启用的。
	//设置这个选项会降低使用更高版本保存的源文件的质量。而那些已经有较低质量的文件。设置将使用无损优化进行压缩。
	
	-n, --noaction
	//不要真的优化文件，只需打印结果。
	
	-S<size>, --size=<size>
	//尝试优化文件大小（禁用了无损优化mizaiont模式）。目标尺寸指定KB（1 N）或百分比（1% - 99%）的原始文件的大小。
	
	-T<treshold>, --threshold=<treshold>
	//如果压缩增益低于阈值（%），则保持文件不变。传输安全有效值为：0 - 100
	
	-o, --overwrite
	//覆盖目标文件，即使它存在（使用D选项）。
	
	-p, --preserve
	//保存文件修改时间。
	
	-q, --quiet
	//安静模式。
	
	-t, --totals
	//处理完所有文件后打印总计。
	
	-v, --verbose
	//启用详细模式(积极聊天).
	
	--all-normal
	//强制所有输出文件为非逐行扫描。可以用来转换所有输入文件的渐进式JPEG当使用--force选项。
	
	--all-progressive
	//强制所有输出文件都是渐进的。可以将所有输入文件正常（非连续）当使用--force选项的JPEG文件。
	
	--strip-all
	//去除所有（Comment  & Exif）从输出文件删除标记。（注！默认情况下只有Comment  & Exif标记保存，其他一切都是丢弃）
	
	--strip-com
	//从输出文件中删除Comment(COM)标记。
	
	--strip-exif
	//从输出文件中删除标记。
	
	--strip-iptc
	//从输出文件中删除IPTC标记。
	
	--strip-icc
	//将ICC配置文件从输出文件中删除。
```

官方文档：https://www.kokkonen.net/tjko/src/man/jpegoptim.txt

### 2. optipng 

#### 1. 基础命令

只能压缩`png`、`bmp`类型

```bash
# 默认指令
optipng tupian.png

# 高级压缩率无损压缩（太慢）
optipng -o7 -zm1-9 tupian.png

# 批量文件大于500k的图片压缩
find ./路径 -name '*.png' -size +500 | xargs optipng
```

#### 2. 其他参数

```config
NAME
	OptiPNG−优化便携式网络图形文件

SYNOPSIS
	optipng [−? | −h | −help]
	optipng [options...] files...

DESCRIPTION
	OptiPNG程序将尝试优化PNG文件，即将其大小减小到最小值。失去语义信息。此外，该程序还应执行一套辅助功能。完整性检查、元数据恢复和pixmapto - png转换。
	优化尝试不能保证成功。有效的PNG文件不能被这个程序优化，通常是原封不动的，它们的大小不会增长。用户可以请求重写此默认行为。

FILES
	输入文件是用PNG格式(本机格式)或外部格式编码的光栅图像文件。当前支持的外部格式是GIF、BMP、PNM和TIFF。
      OptiPNG处理命令行中给出的每个图像文件如下:
	      −如果是PNG格式的图像:
	        试图优化给定文件的位置。如果优化是成功的，或者选择−力被激活，其优化的版本替换原来的文件。原始文件备份，如果选择−保持启用。
	      −如果图像是一个外部格式：
	        创建给定文件的优化PNG版本。输出文件名由原始文件名和PNG扩展名组成。
	      现有的文件不会被覆盖，除非该选项启用−clobber

OPTIONS：

	−?, −h, −help //显示选项的完整摘要。
	
	−backup, −keep //对修改后的文件进行备份。
	
	−clobber //覆盖现有的输出和备份文件。在这个选项，如果选择−backup 未启用，覆盖旧的备份文件的删除。
	
	−dir directory //将输出文件写入目录。
	
	−fix //启用错误恢复。此选项对有效的输入文件没有影响。
	//程序将花费大量的精力在不增加输出文件大小的情况下尽可能地恢复尽可能多的数据，但不能保证成功。该程序可能会增加文件的大小，例如，重建丢失的关键数据。在此选项下，完整性应优先于文件大小。
	//当此选项未被使用时，无效的输入文件将被未处理。
	
	−force //强制编写新的输出文件。
	//此选项覆盖程序的决定不写这样的文件，例如当PNG输入数字签名（使用dsig），或当PNG输出变得大于PNG输入。
	
	−log file //将消息记录到文件。出于安全原因，文件必须有扩展名。此选项已被废弃，最终将被删除。使用shell重定向。
	
	−out file //将输出文件写入文件。命令行必须只包含一个输入文件。
	
	−preserve //保存（文件属性的文件访问时间邮票，在人权等）适用。
	
	−quiet, −silent // 在安静的运行模式。
	
	−simulate //运行模拟模式：执行测试，但不创建输出文件。
	
	−v //启用该选项 −verbose and −version.
	
	−verbose  //在详细模式运行。
	
	−version //显示版权，版本和建立信息。
	
	−− //选择开关停止解析。
	PNG编码和优化选项。
	
	−o level //选择优化级别
	//优化level0enables一组优化操作，需要最少的努力。将不会有任何变化的图像的属性一样，比特深度或颜色的类型，并没有再压缩现有IDAT数据流。
	//优化level1enables单IDAT压缩试验。试验选择的是什么，OptiPNG认为这可能是最有效的。
	//优化level2和更高的使多个IDAT压缩试验；此选项的行为和默认值可能会在不同的程序版本中发生更改。使用选项−H看到有关您的特定版本。
	
	−f filters //选择PNG增量过滤器。
	//过滤器的参数被指定为一个rangeset（例如−F0−5），和默认的过滤器值取决于设置的选项−O.优化水平过滤器的值0, 1, 2，3和4显示静态滤波，和对应的标准PNG过滤代码（无，左，上，平均和Paeth，分别）。滤波值5表明自适应滤波，其作用是通过libpng的定义（3）用optipng。
	
	−full //制作一份关于IDAT的完整报告。这种选择可能会减缓试验的速度。
	
	−i type //选择交错类型(0−1)。
	
	//如果交错式0被选择，输出图像应非隔行扫描（即progressivescanned）。如果交错式1被选择，输出图像应交错使用adam7方法。默认情况下，输出应具有相同的类型作为输入接口。
	
	−nb //不要应用位深度还原。
	
	−nc //不要使用颜色类型还原。
	
	−np //不应用调色板还原。
	
	−nx //不适用任何无损图像还原:启用选项−nb,-nc控和−−np。
	
	−nz //不记录IDAT数据流
	
	−zc levels //选择IDAT压缩中使用的zlib压缩级别。
	
	−zm levels //选择IDAT压缩中使用的zlib内存级别。
	
	−zs strategies //选择在IDAT压缩中使用的zlib压缩策略。
	
	−zw size //选择zlib窗口大小(32 k,16 k、8 k、4 k,2 k,1 k,512256)中使用IDAT压缩。
	
	−snip //从多图像、动画或视频文件中删除一个图像。
	
	−strip objects //从PNG文件中删除元数据对象。
```

官方文档：[http://optipng.sourceforge.net/optipng-0.7.7.man.pdf](http://optipng.sourceforge.net/optipng-0.7.7.man.pdf)