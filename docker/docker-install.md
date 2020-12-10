# docker 安装

1. 查看是否已安装 docker 列表

   `yum list installed | grep docker`

2. 安装 docker

   `yum -y install docker`

 3. 启动 docker

    `systemctl start docker`

4. 查看 docker 服务状态

   `systemctl status docker`

5. docker 容器访问宿主机IP可通过 `ifconfig` 查看，linux下一般是 172.17.0.1 , macOS下一般是 192.168.65.1

