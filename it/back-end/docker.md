# Docker

## 1 Linux 通用

## 2 Centos

### 2.1 Centos 7

#### 2.1.1 安装

```
# 卸载旧的
yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-selinux \
                  docker-engine-selinux \
                  docker-engine \
                  docker-ce

# 安装
yum install -y yum-utils \
           device-mapper-persistent-data \
           lvm2 --skip-broken

# 设置docker镜像源
yum-config-manager \
    --add-repo \
    https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo
    
sed -i 's/download.docker.com/mirrors.aliyun.com\/docker-ce/g' /etc/yum.repos.d/docker-ce.repo

yum makecache fast

yum install -y docker-ce
```

#### 2.1.2 常用命令

```
# 关闭
systemctl stop firewalld
# 禁止开机启动防火墙
systemctl disable firewalld
# 查看防火墙状态是否被关闭
systemctl status firewalld

# 启动docker服务
systemctl start docker
# 停止docker服务
systemctl stop docker
# 重启docker服务
systemctl restart docker

docker -v
```

#### 2.1.3 镜像操作

```
hub.docker.com
docker pull xxx
docker images
docker rmi xxx
docker save -o aaa.tar image xxx:latest
docker load -i aaa.tar
```

#### 2.1.4 容器操作

```
# 创建并启动一个容器
# aaa 容器名称，-d 后台运行，-p 宿主机到容器的端口映射
# xxx 镜像名称
docker run --name aaa -d -p 80:80 xxx

docker ps [-a]
docker start xxx
docker stop xxx
docker rm xxx

# 进入容器执行指令
# -it 创建一个标准输入、输出的终端，允许我们指令交互
# aaa 容器名称
# bash 执行指令
docker exec -it aaa bash
# 或 docker exec -it aaa 指令名称

# 1、容器是精简的、只适合对应镜像的linux系统。
# 所以，很多东西是没有的，例如vim。
# 2、容器内有独立的文件系统。
```

#### 2.1.5 数据卷操作

```
docker volume [cmd]
# cmd:
# create 创建volume
# inspect 显示一个/多个volume信息
# ls 列出所有的volume
# prune 删除未使用的volume
# rm 删除一个/多个volume

# 挂载-宿主目录映射到容器目录
docker run --name aaa -v hostddd:/ddd -d -p 80:80 xxx
```

## 3 Ubuntu
