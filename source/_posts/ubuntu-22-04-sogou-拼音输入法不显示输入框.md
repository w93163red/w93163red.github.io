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

如果直接运行时，出现依赖问题：
```
/opt/sogoupinyin/files/bin/sogoupinyin-service: symbol lookup error: /opt/sogoupinyin/files/bin/../lib/libSogouShell.so: undefined symbol: qt_version_tag, version Qt_5.6
```
直接使用系统自带的qt包进行替换：
```
sudo cp /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5Qml.so.5
sudo cp /usr/lib/x86_64-linux-gnu/libQt5DBus.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5DBus.so.5
sudo cp /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5Gui.so.5
sudo cp /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5Widgets.so.5
sudo cp /usr/lib/x86_64-linux-gnu/libQt5Core.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5Core.so.5
sudo cp /usr/lib/x86_64-linux-gnu/libQt5Network.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5Network.so.5
sudo cp /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5Quick.so.5
sudo cp /usr/lib/x86_64-linux-gnu/libQt5QuickWidgets.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5QuickWidgets.so.5
sudo cp /usr/lib/x86_64-linux-gnu/libQt5Svg.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5Svg.so.5
sudo cp /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5Qml.so.5
sudo cp /usr/lib/x86_64-linux-gnu/libQt5XcbQpa.so.5 /opt/sogoupinyin/files/bin/../lib/qt5/lib/libQt5XcbQpa.so.5
```