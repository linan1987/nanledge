# Nginx

## 1 Linux

### 1.1 通用

```
# 配置文件(第2个是虚拟机配置文件)
# /etc/nginx/nginx.conf
# /etc/nginx/sites-available/default

# 命令
sudo systemctl start nginx
sudo systemctl restart nginx
```

### 1.2 Centos

```
// sudo yum install epel-release
// sudo yum update
1 查询可用的版本并下载
yum list nginx
sudo yum install nginx-x.x.x

2 启动服务
sudo systemctl start nginx

3 开机自启
sudo systemctl enable nginx

4 配置文件
/etc/nginx/nginx.conf

5 如果端口被selinux拦截，则需手动添加端口。
SELinux 是一种 Linux 安全模块，用于限制进程的访问权限，以保护系统安全。
nginx 服务启动失败是因为 SELinux 拒绝了 /usr/sbin/nginx 进程在端口 8847 上进行 name_bind 操作。
systemctl status nginx.service
journalctl -xe
（1）semanage port -a -t http_port_t -p tcp 8809 将8809设置为http服务端口（此时无需执行setsebool -P nis_enabled 1）
或
（2）semanage port -a -t port_t -p tcp 8809 将8809设置为普通服务端口（此时必须执行setsebool -P nis_enabled 1）
setsebool -P nis_enabled 1
```

### 1.3 Ubuntu

```
```

## 2 Windows

```
# 启动nginx
start nginx

# 修改配置后重新加载生效
./nginx.exe -s reload

# 快速停止nginx,可能并不保存相关信息
./nginx.exe -s stop

# 完整有序的停止nginx,并保存相关信息
./nginx.exe -s quit

# 按照指定配置去启动nginx
./nginx.exe -c conf/nginx.conf

# 检测nginx是否配置正确
./nginx.exe -t -c conf/nginx.conf
```