# 构建说明

## 获取blob

**Block-based文件：**各分区内容作为二进制数据存储在多个*.dat.br文件中，具体可查看*.transfer.list文件。

## 提取镜像

安装依赖brotli

解压

```sh
unzip path system.transfer.list system.new.dat*
unzip path vendor.transfer.list vendor.new.dat*
brotli --decompress --output=system.new.dat system.new.dat.br
brotli --decompress --output=vendor.new.dat vendor.new.dat.br
```

选择构建目标

```sh
git clone https://github.com/xpirt/sdat2img
```

提取镜像

```sh
python sdat2img/sdat2img.py system.transfer.list system.new.dat system.img
python sdat2img/sdat2img.py vendor.transfer.list vendor.new.dat vendor.img
```

## 挂载镜像并提取blob

```sh
./extract-files.sh path
```