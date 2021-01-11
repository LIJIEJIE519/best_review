# Docker

![https://www.runoob.com/wp-content/uploads/2016/04/576507-docker1.png](https://www.runoob.com/wp-content/uploads/2016/04/576507-docker1.png)

| Docker              | 面向对象 |
| ------------------- | -------- |
| 容器                | 对象     |
| 镜像/类似Ubuntu系统 | 类       |



### 1. 安装教程

https://www.runoob.com/docker/ubuntu-docker-install.html

镜像加速服务

https://cr.console.aliyun.com/cn-hangzhou/instances/mirrors

```
sudo systemctl daemon-reload
sudo systemctl restart docker
```

#### 2. 运行命令

```
docker run ubuntu:15.10 /bin/echo "Hello world"

docker: Docker 的二进制执行文件。
run: 与前面的 docker 组合来运行一个容器。
ubuntu:15.10 指定要运行的镜像，Docker 首先从本地主机上查找镜像是否存在，如果不存在，Docker 就会从镜像仓库 Docker Hub 下载公共镜像。
/bin/echo "Hello world": 在启动的容器里执行的命令

Docker 以 ubuntu15.10 镜像创建一个新容器，然后在容器里执行 bin/echo "Hello world"，然后输出结果。


docker ps

docker run -it ubuntu /bin/bash			//参数为以命令行模式


docker export 1e560fca3906 > ubuntu.tar    // 导出本地某个容器
```

