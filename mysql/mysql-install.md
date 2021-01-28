# mysql 安装

## 一、 删除老版本 mysql

1. 执行yum命令，删除 mysql 的lib库

   `yum remove mysql mysql-server mysql-libs mysql-server`

2. 检测系统是否自带 mysql 和 mariadb，如果有就删除它 `yum remove 文件名`

   `rpm -qa | grep mysql`

   `rpm -qa | grep mariadb`

3. 执行find命令，查找 mysql  的残留文件，然后运行 `rm -rf 文件名` 删除残留的 mysql 文件

   `find / -name mysql`



## 二、安装 mysql

1. 进入目录 `/usr/local`

   `cd /usr/local`

2. 上传 mysql 压缩包 mysql-5.7.31-linux-glibc2.12-x86_64.tar.gz

3. 解压 mysql-5.7.31-linux-glibc2.12-x86_64.tar.gz

   `tar -zxvf mysql-5.7.31-linux-glibc2.12-x86_64.tar.gz`

4. 更名

   `mv mysql-5.7.31-linux-glibc2.12-x86_64 mysql`

5. 检查 mysql 用户组和用户是否存在，如果没有，则创建

   `cat /etc/group | grep mysql`

   `cat /etc/passwd |grep mysql`

   `groupadd mysql`

   `useradd -r -g mysql mysql`

   

   

6. 在 `/usr/local/mysql` 目录下创建data目录

   `mkdir mysql/data`

7. 更改 mysql 目录下所属的用户组和用户，以及权限

   `chown -R mysql:mysql /usr/local/mysql`

   `chmod -R 755 /usr/local/mysql`

8. 创建配置文件 `/etc/my.cnf`

   ```
         [mysqld]
         port=3306
         user=mysql
         basedir=/usr/local/mysql
         datadir=/usr/local/mysql/data
         socket=/tmp/mysql.sock
         character_set_server=utf8mb4
         symbolic-links=0
         explicit_defaults_for_timestamp=true
         [client]
         default-character-set=utf8
         [mysql]
         default-character-set=utf8
         [mysqld_safe]
         log-error=/usr/local/mysql/data/mysql.log
         pid-file=/usr/local/mysql/data/mysql.pid
   ```

9. 初始化数据库

   `cd mysql/bin`

   `./mysqld  --defaults-file=/etc/my.cnf --user=mysql --basedir=/usr/local/mysql/ --datadir=/usr/local/mysql/data/ --initialize`

   * 如果报错：`./mysqld: error while loading shared libraries: libaio.so.1: cannot open shared object file: No such file or directory`，需要查看并安装libaio包，再重新初始化数据库

     `rpm -qa | grep libaio`

     `yum -y install libaio-devel.x86_64`

10. 保存上一步日志最后的初始化密码 （`root@localhost: 8n7GjpOtYw&y`）

11. 添加软连接

    `ln -s /usr/local/mysql/support-files/mysql.server /etc/init.d/mysql`

    `ln -s /usr/local/mysql/bin/mysql /usr/bin/mysql`

12. 启动mysql服务器

    `service mysql start`

13. 用第10步保存的密码登录 mysql，并初始化密码

    `mysql -u root -p`

    `set password for root@localhost = password('123456');`

14. 开放远程连接

    `use mysql;`

    `update user set Host='%' where User='root';`

    `flush privileges;`

15. 重新修改密码
   `set password for 'root'@'%' = password('密码');`
