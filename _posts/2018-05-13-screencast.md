---
layout: post
title: "在屏幕上显示敲击的键盘 screencast"
tagline: ""
description: ""
category: 经验总结
tags: [screencast, keyboard, linux, ]
last_updated: 
---

之前在做一次 Vim 演示的时候想要更加直观的在屏幕上实时显示出当前敲击的字母，所以找到了 screencast 这个解决方法。

## 安装
在[GitHub发布页面](https://github.com/wavexx/screenkey/releases) 下载安装包

    wget "https://github.com/wavexx/screenkey/archive/screenkey-0.9.tar.gz"
    tar xvf screenkey-0.9.tar.gz
    # 安装依赖
    sudo apt-get install python-gtk2 python-setuptools python-setuptools-git python-distutils-extra

然后执行安装

    sudo ./setup.py install

然后启动

    screenkey

## 使用

然后可以设置各种参数，延迟时间，字体，大小，颜色，透明度等等

## reference

- <https://github.com/wavexx/screenkey>
- <https://www.thregr.org/~wavexx/software/screenkey/index.html>
