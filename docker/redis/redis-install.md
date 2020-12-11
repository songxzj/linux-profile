# redis 安装

## 安装

1. 获取 redis 官方镜像

   `docker pull redis:6.0.9`

2. 进入目录 `/usr/local`，创建 redis 文件夹并进入

   * 放入 [redis.conf](conf/redis.conf) 文件

   * 创建 `data` 文件夹

3. 挂载宿主机配置文件启动 redis

   `docker run -p 6379:6379 --name myredis -v /usr/local/redis/redis.conf:/etc/redis/redis.conf -v /usr/local/redis/data:/data -d redis:6.0.9 redis-server /etc/redis/redis.conf --appendonly yes --requirepass "123456"`

4. 可通过 `docker exec -it myredis redis-cli -a 123456` 进入 redis 客户端命令

   

## 配置文件

1. redis.conf 主要配置
   * `bind 127.0.0.1` #这是限制redis只能本地访问，注释掉这部分可通过其他 ip 访问
   * `protected-mode yes` #默认yes，开启保护模式，限制为本地访问，可改为 no 关闭
   * `daemonize no` #默认no，改为yes意为以守护进程方式启动，可后台运行，除非kill进程，改为yes会使配置文件方式启动redis失败
   * `tcp-keepalive 300` #防止出现远程主机强迫关闭了一个现有的连接的错误 默认是300
   * `databases 16` #数据库个数（可选）
   * `dir  ./` #输入本地redis数据库存放文件夹（可选）
   * `appendonly yes` #redis持久化（可选）
   * `requirepass  密码` #配置redis访问密码（可选）

   