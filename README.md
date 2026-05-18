[中文](./README_CN.md)

# Introduction
This project provides a one-click script to build SpacemiT K3 Debian 13 images that are ready to use out of the box. Currently supports building GNOME, XFCE and Minimal images.

# GNOME Image


<img width="1920" height="1080" alt="GNOME" src="https://github.com/user-attachments/assets/eb399d65-6ffe-4788-9e86-f1724edda2a4" />



## Features
- Pre-installed native GNOME desktop with GPU support
- Pre-installed Chromium browser with hardware video decoding support
- Pre-installed common toolkits: vim, ssh, iproute2, wget
- Pre-configured [SpacemiT K3 Debian software sources](http://archive.spacemit.com/debian/)
- Wi-Fi and Ethernet support

## Features Not Yet Adapted
- GStreamer framework
- Video applications
- Camera applications

# XFCE Image


<img width="1920" height="1080" alt="XFCE" src="https://github.com/user-attachments/assets/4ca69197-89c1-4772-89e1-b0874bffeca2" />



## Features
- Pre-installed native XFCE desktop (GPU is not supported yet)
- Pre-installed common toolkits: vim, ssh, iproute2, wget
- Pre-configured [SpacemiT K3 Debian software sources](http://archive.spacemit.com/debian/)
- Wi-Fi and Ethernet support

## Features Not Yet Adapted
- GStreamer framework
- Video applications
- Camera applications

# Supported Hardware
- K3-Pico-ITX
- K3-Com260

# Image Download
- Official: [Link](https://archive.spacemit.com/image/k3/version/debian/)

# Flashing
- SD Card Raw Image

  Files ending with `.img.gz` can be decompressed and written to SD card using [balenaEtcher](https://etcher.balena.io/), or written using the dd command after decompression.

- Custom Image

  Files ending with `.tar.gz` can be flashed using Titan Flasher, or extracted and flashed using fastboot.

Firmware `root` user password: `bianbu`

XFCE image initial username: `user`, password: `bianbu`

For Titan Flasher flashing, please refer to the [Flashing Tool User Manual](https://developer.spacemit.com/documentation?token=O6wlwlXcoiBZUikVNh2cczhin5d).

# Creating Your Own Image
If you want to create your own image, you can customize it following the steps below.

## Environment Preparation
You need an X86 PC, preferably running Ubuntu LTS version, such as Ubuntu 24.04.

If you have a K3 development board, we recommend building on a Bianbu V4.x system instead.

## Installing Dependencies
Image creation requires qemu. You can use our one-click installation script (requires sudo privileges):

```shell
bash <(wget -qO- https://archive.spacemit.com/qemu/install_qemu_user_riscv64.sh)
```

## Image Creation

First, clone the build script to your local machine:

```
git clone git@github.com:jing-liu-spacemit/debian-builder.git
git checkout -b k3-main
```

You can run the following command to create all three images simultaneously:
```bash
sudo ./debian-image-create.sh
```
You can also specify parameters:

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

# Issue Reporting
Your feedback drives our iterations. Please submit issue reports in Issues, including the development board model, reproduction steps, and logs.

# Contributing
We welcome developers to contribute code and documentation.

To maximize the chances of your pull request being accepted, please follow these guidelines:

1. Write unit tests for all bug fixes and new features. If your code doesn't have tests, it won't be merged.
2. Minimize the number of changes in each pull request. Try to solve one problem at a time.
3. Use [conventional commit messages](https://www.conventionalcommits.org/en/v1.0.0/) as pull request titles. Examples:
   - New feature: `feat: adding foo API`
   - Bug fix: `fix: issue with foo API`
   - Documentation change: `docs: adding foo API documentation`

# TODO
