# 单机Redis安装

## 1.下载

`wget http://download.redis.io/releases/redis-4.0.9.tar.gz`

## 2.安装依赖

`yum install gcc-c++`

## 3.安装

```shell
$ tar xzf redis-4.0.9.tar.gz
$ cd redis-4.0.9
$ yum -y install gcc-c++
$ make 
#如果报错,则运行make MALLOC=libc
$ make PREFIX=/opt/soft/redis install
```

## 4 运行

```shell
$ ulimit -a  
$ ulimit -n 10032 
$ vi /etc/security/limits.conf
$ ./redis-server redis.conf
```

