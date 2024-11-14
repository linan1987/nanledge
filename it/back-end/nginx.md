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

### 1.3 Ubuntu

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