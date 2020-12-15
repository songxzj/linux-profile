# nginx 安装

## 安装

1. 获取 nginx 官方镜像

   `docker pull nginx:1.19.5`

2. 进入目录 `/usr/local`，创建 nginx 文件夹并进入

   * 创建  `html`, `log` 文件夹
   * 放入 [conf](conf) 文件夹

3. 挂载宿主机配置文件启动 nginx

   `docker run --name mynginx -p 80:80  -v /usr/local/nginx/log:/var/log/nginx -v /usr/local/nginx/conf/nginx.conf:/etc/nginx/nginx.conf -v /usr/local/nginx/conf/conf.d:/etc/nginx/conf.d -v /usr/local/nginx/html:/usr/share/nginx/html -d nginx:1.19.5`

## 配置

1. 修改配置只需修改 `/usr/local/nginx/conf/conf.d` 下的 `default.conf`；或者新增 `*.conf` 文件在此目录下，重启 nginx 容器
