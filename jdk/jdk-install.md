# JDK 安装
1. 进入目录 `/usr/local`;
`cd /usr/local`
2. 创建文件夹 java;
3. 进入目录 `/java`;
`cd java`
4. 上传 jdk 压缩包 jdk-8u271-linux-x64.tar.gz;
5. 解压 jdk-8u271-linux-x64.tar.gz;
`tar -zxvf jdk-8u271-linux-x64.tar.gz`
6. 配置环境变量
	1. 编辑文件 `vim /etc/profile`
	2. 键入 `i` 追加
```
JAVA_HOME=/usr/local/java/jdk1.8.0_271
PATH=$PATH:$JAVA_HOME/bin
CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export JAVA_HOME CLASSPATH PATH
```
	3. 键入 `:wq` 保存退出
7. 刷新环境变量
`source /etc/profile`
8. 查看是否安装成功
`java -version`
