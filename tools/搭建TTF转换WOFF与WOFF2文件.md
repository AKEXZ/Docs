# 搭建TTF转换WOFF与WOFF2文件

## WOFF

开始之前请先自行搭建git，WOFF需要安装npm环境。

### 介绍

Web开放字体格式（Web Open Font Format，简称WOFF）是一种网页所采用的字体格式标准。此字体格式不但能够有效利用压缩来减少档案大小，并且不包含加密也不受DRM（数位著作权管理）限制

### 构建

```bash
git clone --recursive https://github.com/fontello/ttf2woff.git
cd ttf2woff
npm install
./ttf2woff.js 文件名.{ttf,woff}    #方法2 ./ttf2woff 文件名.ttf 文件名.woff
```

## WOFF2

### 介绍

WOFF 2.0格式类似于WOFF 1.0格式，但改进了压缩功能，减少网络带宽的使用。WOFF 2.0基于Brotli压缩算法，该算法是用于提高Web浏览速度的开源数据压缩库。WOFF2文件比WOFF文件小30％。

### 环境

程取决于 g++ 编译器，在标准库中构建：

```bash
git clone --recursive https://github.com/google/woff2.git
cd woff2
make clean all
```

如果您的系统上已经安装了Brotli，则可以使用CMake来构建可执行文件和库：

```bash
git clone https://github.com/google/woff2.git
cd woff2
mkdir out
cd out
cmake
make
make install
```

默认情况下，将生成公共库。要使用静态链接，请执行以下操作：

```bash
cd woff2
mkdir out-static
cmake -DBUILD_SHARED_LIBS=OFF
make
make install
```

### 构建

```bash
./woff2_compress 文件名.ttf
./woff2_decompress 文件名.woff2
```

## 其他

### 参考资料

[https://github.com/fontello/ttf2woff](https://github.com/fontello/ttf2woff)

[https://github.com/google/woff2](https://github.com/google/woff2)