# Docker

## 1 简介

**Docker**是一个开源的应用容器引擎

Docker支持将软件编译成一个镜像；然后在镜像中各种软件做好配置，将镜像发布出去，其他使用者可以直接使用这个镜像；

运行中的这个镜像称为容器，容器启动是非常快速的。

## 2 Docker核心概念

### 2.1 docker主机(Host)

安装了Docker程序的机器（Docker直接安装在操作系统之上）

### 2.2 docker客户端(client)

连接docker客户端通过命令行或者图形化界面操作docker守护进程通信

### 2.3 docker仓库(Registry)

用来保存各种打包好的软件镜像

### 2.4 docker镜像(images)

软件打包好的镜像；放在docker仓库中

### 2.5 docker容器（Container）

镜像启动后的实例称为一个容器；容器是独立运行的一个或一组应用



使用docker的步骤；

1.安装docker

2.去docker仓库找到这个软件对应的镜像

3.直接使用docker运行这个镜像，这个镜像就会生成一个docker容器

4.对容器的启动停止，就是对软件的启动停止

## 3 安装Docker

### 3.1 安装Linux虚拟机

#### 3.1.1 安装虚拟机

#### 3.1.2 在虚拟机里安装操作系统 

#### 3.1.3 连接虚拟机进行操作

#### 3.1.4 设置虚拟机网络

桥接网络--> 选好网卡(无线有个viewlis)--> 接入网线;

#### 3.1.5 重启虚拟机的网络

#### 3.1.6 查看IP

```shell
ip addr
```



### 3.2 在虚拟机上安装docker

### 3.1 查看内核版本

```shell
uname -r
```

查看内核版本，如果内核版本小于3.10，走下一步，否则跳过下一步

### 3.2 升级内核

```shell
yum update
```

### 3.3 安装docker

安装docker

```shell
yum -y install docker
```

直到出现complete!

### 3.4 启动docker

`systemctl start docker`

#### 3.5 设置开机启动

```shell
systemctl enable docker #开机启动
systemctl stop docker #停止
```

## 4 使用docker

### 4.1 搜索镜像

```shell
docker search mysql
```

或者在dockerhub 搜索

### 4.2 下载docker镜像

doclek pull 

```shell
docker pull mysql
```

4.3 查看所有的镜像

```shell
docker images
```

### 5 容器操作

docker ru