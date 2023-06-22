---
title: ubuntu 22.04 sogou 拼音输入法不显示输入框
date: 2023-06-21 21:17:39
tags: 
	- Linux
---

ubuntu 下搜狗输入法在安装完官方的deb包之后仍然不显示输入框。
需要安装如下的依赖：
```
sudo apt install libqt5qml5 libqt5quick5 libqt5quickwidgets5 qml-module-qtquick2
sudo apt install libgsettings-qt1
```
