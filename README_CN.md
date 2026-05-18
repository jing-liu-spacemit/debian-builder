[English](./README.md)

# 简介
本项目提供一键构建 SpacemiT K3 Debian 13 镜像的脚本，镜像开箱即用。目前支持构建 GNOME、XFCE和Minimal 镜像。

# GNOME 镜像


https://github.com/user-attachments/assets/53808a85-537f-4502-a669-539c963ae0e9


## 特性
- 预装原生 GNOME 桌面，支持GPU
- 预装 Chromium 浏览器，支持视频硬件解码
- 预装常见工具包：vim、ssh、iproute2、wget
- 预置 [SpacemiT K3 debian 软件源](http://archive.spacemit.com/debian/)
- 支持 Wi-Fi、Ethernet

## 尚未适配的功能
- GStreamer框架
- 视频应用
- 相机应用

# XFCE 镜像


https://github.com/user-attachments/assets/74c713ce-ddd6-481e-bc52-27d0fdc78ed1


## 特性
- 预装原生 XFCE 桌面（暂不支持GPU）
- 预装常见工具包：vim、ssh、iproute2、wget
- 预置 [SpacemiT K3 debian 软件源](http://archive.spacemit.com/debian/)
- 支持 Wi-Fi、Ethernet

## 尚未适配的功能
- GStreamer框架
- 视频应用
- 相机应用

# 支持的硬件
- K3-Pico-ITX
- K3-Com260

# 镜像下载
- 官方：[链接](https://archive.spacemit.com/image/k3/version/debian/)

# 刷机
- sdcard raw 镜像

  以 `.img.gz` 结尾，解压后可以用[balenaEtcher](https://etcher.balena.io/)写入 sdcard，或者解压后用 dd 命令写入 sdcard。

- 自定义镜像

  以 `.tar.gz` 结尾，可以用 Titan Flasher 刷机，或者解压后用 fastboot 刷机。

固件`root`用户的密码：`bianbu`

XFCE镜像初始用户名：`user`，密码：`bianbu`

Titan Flasher刷机参考[刷机工具使用手册](https://developer.spacemit.com/documentation?token=O6wlwlXcoiBZUikVNh2cczhin5d)。

# 制作自己的镜像
如果您要做自己的镜像，可以按照下面步骤定制。

## 环境准备
您需要一个X86的PC，推荐安装Ubuntu LTS版本，例如Ubuntu 24.04。

如果您拥有K3开发板的话，我们更推荐在Bianbu V4.x版本系统上制作。

## 安装依赖
制作镜像需要安装qemu。可以使用我们提供的一键安装脚本（需要有sudo权限）：

```shell
bash <(wget -qO- https://archive.spacemit.com/qemu/install_qemu_user_riscv64.sh)
```

## 镜像制作

先将制作脚本下载到本地：

```
git clone git@github.com:jing-liu-spacemit/debian-builder.git
git checkout -b k3-main
```

您可以运行下面指令来同时制作三种镜像：
```bash
sudo ./debian-image-create.sh
```
也可以通过参数来指定：

- Minimal
```bash
sudo ./debian-image-create.sh Minimal
```

- GNOME
```bash
sudo ./debian-image-create.sh GNOME
```

- XFCE
```bash
sudo ./debian-image-create.sh XFCE
```

# 问题反馈
您的反馈是我们迭代的动力，请在 Issues 提交问题报告，并注明开发板型号、复现步骤和日志。

# 参与贡献
我们欢迎开发者贡献代码与文档。

为了最大程度地让你的拉取请求被接受，请遵循以下指导原则：

1. 对所有错误修复和新功能进行单元测试。如果你的代码没有测试，它将不会被合并。
2. 尽量减少每个拉取请求中的更改数量。尽可能一次解决一个问题。
3. 使用 [conventional commit messages](https://www.conventionalcommits.org/en/v1.0.0/) 作为拉取请求标题。示例：
- 新功能：`feat: adding foo API`
- 错误修复：`fix: issue with foo API`
- 文档更改：`docs: adding foo API documentation`

# TODO
