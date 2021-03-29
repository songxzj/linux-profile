# yum mysql 安装

## 一、 下载 rpm 包

1. 下载 rpm 包，(mysql 查询地址)[https://dev.mysql.com/downloads/repo/yum/]

  `wget https://repo.mysql.com/mysql80-community-release-el7-3.noarch.rpm`

2. 安装 rpm 包

  `yum install -y mysql80-community-release-el7-1.noarch.rpm`

3. 选择具体版本

  `yum repolist all | grep mysql`      // 查看 YUM 仓库关于 MySQL 的所有仓库列表

  `yum repolist enabled | grep mysql`  // 只查看启用的

4. 关闭80，开启57

  `yum install yum-utils`                             // 安装 YUM 管理工具包，此包提供了 yum-config-manager 命令工具

  `yum-config-manager --disable mysql80-community`    // 禁用 8.0

  `yum-config-manager --enable mysql57-community`     // 启用 5.7

5. 再次确认启动MySQL5.7
 
  `yum repolist enabled | grep mysql`



## 二、安装 mysql

1. 安装

  `yum install -y  mysql-community-server`

2. 管理 mysql 服务
  
  `systemctl start mysqld.service`  // 启动

  `systemctl status mysqld.service` // 查看状态

  `systemctl enable mysqld`         // 开机自启动

  `ss -natl |grep 3306`             // 查看监听端口，默认 3306

3. 初始化 mysql

  `grep 'temporary password' /var/log/mysqld.log`

4. 用第3步保存的密码登录 mysql，并初始化密码

  `mysql -u root -p`

  `set password for root@localhost = password('密码');`

5. 开放远程连接

  `use mysql;`

  `update user set Host='%' where User='root';`

  `flush privileges;`
