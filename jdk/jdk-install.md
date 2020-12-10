# JDK 安装

## 安装 jdk

1. 进入目录 /usr/local

   `cd /usr/local`

2. 创建目录 java 并进入此目录

   `mkdir java`

   `cd java`

3. 上传 jdk 压缩包 jdk-8u271-linux-x64.tar.gz

4. 解压 jdk-8u271-linux-x64.tar.gz

   `tar -zxvf jdk-8u271-linux-x64.tar.gz`

5. 配置环境变量

   * 编辑文件 `vim /etc/profile`

   * 键入 `i` 追加

     ```
     JAVA_HOME=/usr/local/java/jdk1.8.0_271
     PATH=$PATH:$JAVA_HOME/bin
     CLASSPATH=.:$JAVA_HOME/jre/lib/rt.jar:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
     export JAVA_HOME CLASSPATH PATH
     ```

   * 键入 `:wq` 保存退出

6. 刷新环境变量

   `source /etc/profile`

7. 查看是否安装成功

   `java -version`
