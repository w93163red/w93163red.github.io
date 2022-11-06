---
title: java pathfinder + symbc 踩坑记
date: 2022-11-05 17:01:54
tags:
    - concolic execution
    - java pathfinder
---
jpf-core: https://github.com/javapathfinder/jpf-core

jpf-symbc: https://github.com/SymbolicPathFinder/jpf-symbc

我改了一下中间不能跑的intellij代码，也上传了idea的相关配置，路径需要根据自己的机器环境进行配置

https://github.com/w93163red/jpf-core

https://github.com/w93163red/jpf-symbc


记录一下配置java pathfinder 和 symbolic javapathfinder的过程。

jpf 是基于gradle的，symbolic 基于ant + eclipse。

但是我不用eclipse，所以记录一下配置过程，省的之后重新配的时候又重新踩坑。

配置环境: Windows 11 22H2 + WSL2 Ubuntu 22.04

剩下的步骤全部在linux下执行。


1. 验证下java 版本，官方说明只支持java 1.8.
```shell
java -version
```
2. 在$HOME 路径下创建.jpf， 并且配置上site.properties, 指明jpf-core 和 jpf-symbc 的路径
```shell
# cat ~/.jpf/site.properties
jpf-core = /home/ling/code/pathfinder/jpf-core
jpf-symbc = /home/ling/code/pathfinder/jpf-symbc
extensions = ${jpf-core},${jpf-symbc}
```

3. 因为symb-c 依赖于jpf 编译后的产物，产物路径在jpf-core/build下
```shell
cd jpf-core
gradle build
```
![路径](/img/jpf-path.png)

4. 然后intellij import jpf-symbc，在import成功过后，import jpf-core as modules
https://www.jetbrains.com/help/idea/import-project-from-eclipse-page-1.html#import-project

![intellij 导入项目](/img/jpf-import-project.png)

最后项目结构应该长这样：
![项目结构](/img/jpf-project-structure.png)


5. 对于jpf-symbc 的project structure 配置成如下这样

![jpf-core 配置截图1](/img/jpf-modules-jpf-core.png)

![jpf-core 配置截图2](/img/jpf-modules-jpf-core-2.png)


![jpf-symbc 配置截图1](/img/jpf-symbc.png)

![jpf lib 配置截图](/img/jpf-lib.png)


6. 在jpf-symbc下项目路径下`ant build` 出jar包，然后在RunJPF 下跑这个项目