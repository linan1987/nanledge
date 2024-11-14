# Windows

## 1 系统

### 1.1 基础命令

### 1.2 防火墙

### 1.3 代理

### 1.4 网络/IP

## 2 软件源

## 99 三方库/服务

### 99.1 nginx

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