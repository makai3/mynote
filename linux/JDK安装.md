# JDK在Linux安装



## 1 安装

### 1.1 建立文件夹

`mkdir /opt/soft`把自己的`jdk-8u161-linux-x64.tar.gz`给上传上去

### 1.2 解压

进入目录`cd /opt/soft `

解压`tar -zxvf jdk-8u161-linux-x64.tar.gz`

进入JDK目录`cd jdk1.8.0_161`

查看当前目录`pwd`

### 1.3 配置环境变量

打开环境变量文件`vi /etc/profile`

选中最后一行`ctrl+g`

进入编辑状态`o`

把以下信息写到最后面

```shell
# JDK
JAVA_HOME=/opt/soft/jdk1.8.0_161
JRE_HOME=$JAVA_HOME/jre
PATH=$PATH:$JAVA_HOME/bin
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export JAVA_HOME
export JRE_HOME
export PATH
export CLASSPATH
```

按`:wq`保存退出

之后就是启用了`source /etc/profile`

### 1.4 校验

输入`java -version`如果输出JDK信息就表示正常





