# nginx 安装

## 安装 nginx

1. 创建 `/etc/yum.repos.d/nginx.repo` 文件

2. 输入命令`yum list | grep nginx` 可看到前后变化说明导入文件有效

   ![1](F:\linux中间件\nginx\1.jpg)

   ![2](F:\linux中间件\nginx\2.jpg)

3. yum 安装 nginx 

   `yum -y install nginx-1.22.1-1.el7.ngx`

4. `nginx -v` 查看安装版本

5. 启动 nginx

   `systemctl start nginx`

6. 查看是否启动成功

   `ps -ef | grep nginx`

7. 默认安装位置在 `/etc/nginx`，可全局执行 nginx 命令
