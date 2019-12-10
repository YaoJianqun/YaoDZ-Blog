---
title: JDK安装配置
date: 2019-12-10 19:13:41
tags:
 - 后台环境配置

photos:
 - https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/system-1.jpg
---

本文旨在说明JDK在Windows与Linux系统安装与配置，避免每次都需百度，反而容易踩坑报错。

<!-- more -->

## <font color=#4fc08d>\#</font>部署环境

- 系统 : Centos 6.8 / Windows 10
- JDK : 7u80

## <font color=#4fc08d>\#</font>安装与配置(Windows)

### 环境变量配置

**1.++WIN键 + Q++ 搜索 ++环境变量++ 并打开**

{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/JDK%E9%85%8D%E7%BD%AE/2019-12-10_093823.png %}

<br/>

**2.编辑用户环境变量**

{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/JDK%E9%85%8D%E7%BD%AE/2019-12-10_094055.png %}

<br/>

**3.新建`JAVA_HOME`变量 - 变量值为jdk安装目录**

{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/JDK%E9%85%8D%E7%BD%AE/2019-12-10_094315.png %}

<br/>

**4.编辑`Path`变量**

- 如为列表模式添加 : 
{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/JDK%E9%85%8D%E7%BD%AE/2019-12-10_095047.png %}
```c
%JAVA_HOME%\bin
%JAVA_HOME%\jre\bin
```

- 如为文本模式添加 :
{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/JDK%E9%85%8D%E7%BD%AE/2019-12-10_095220.png %}
```c
%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;
```
**注 :** 如文本模式下，原Path变量结尾没有`;`号，需添加`;`号后写入以上代码。

<br/>

**5.新建`CLASSPATH`变量** 

{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/JDK%E9%85%8D%E7%BD%AE/2019-12-10_095716.png %}

```c
.;%JAVA_HOME%\lib;%JAVA_HOME%\lib\tools.jar
```


**注 :** 注意变量值前的`.`号。

<br/>

**6.配置完毕后点击确认**

<br/>

**7.检验是否安装完毕**

- ++WIN键 + R++打开运行，并输入CMD后回车(如在配置环境变量前已打开CMD，建议配置变量后关闭重新打开CMD命令行) : 
{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/JDK%E9%85%8D%E7%BD%AE/2019-12-10_100757.png %}


- 在 CMD 中输入 java，检测是否输入下图所示 : 
{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/JDK%E9%85%8D%E7%BD%AE/2019-12-10_100933.png %}

- 在 CMD 中输入 javac，检测是否输入下图所示 : 
{% img https://oss-yaodz-source.oss-cn-beijing.aliyuncs.com/Yaodz-Blog/JDK%E9%85%8D%E7%BD%AE/2019-12-10_101044.png %}

- 如输出一致则安装成功

---

## <font color=#4fc08d>\#</font>安装与配置(Linux)

### 安装JDK : 

```shell
sudo rpm -ivh jdk-7u80-linux-x64.rpm
```

<br/>

### 修改环境变量 : 

```shell
vi /etc/profile
#在配置文件末尾加入
#安装路径
export JAVA_HOME=/usr/java/jdk1.7.0_80
export CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin
```

<br/>

### 使配置文件生效

```shell
source /etc/profile
```