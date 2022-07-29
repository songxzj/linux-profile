# redis 安装


## 一、 安装 redis

1. 进入目录 `/usr/local`

   `cd /usr/local`

2. 上传 redis 压缩包 redis-7.0.4.tar.gz

3. 解压 redis-7.0.4.tar.gz

   `tar -zxvf redis-7.0.4.tar.gz`

4. 更名

   `mv redis-7.0.4 redis`
   
5. 执行make命令

   `make`
   
6. 如果make执行报错 '/bin/sh: cc: command not found'，需要安装gcc，安装完毕后清除下刚才的make命令执行结果，然后执行make命令

   `yum install gcc`
   
   `make distclean`
   
    `make`
    
7. 进入目录 `/usr/local/redis`

   * 放入 [redis.conf](conf/redis.conf) 文件

   * 创建 `data` 文件夹
    
8. 安装成功后，进入src

   `cd src`
   
   `make distclean`
   
   `make`

9. 启动 redis

   `./redis-server /usr/local/redis/redis.conf`

## 配置文件参考[docker-redis-install](https://github.com/songxzj/linux-profile/blob/main/docker/redis/redis-install.md)
   
