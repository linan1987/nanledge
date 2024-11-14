# Ubuntu

## 1 系统

### 1.1 基础命令

### 1.2 防火墙

```
# 基本设置
sudo ufw status
sudo ufw enable
sudo ufw disable

# 外来访问默认允许/拒绝
ufw default allow/deny

# 允许/拒绝访问20 tcp 端口
ufw allow/deny 20/tcp

# ufw从/etc/services中找到对应service的端口，进行过滤
ufw allow/deny servicename

# 允许自10.0.1.0/10的tcp封包访问本机的25端口
ufw allow proto tcp from 10.0.1.0/10 to 0.0.0.0 port 25

# 删除以前定义的"允许/拒绝访问20端口"的规则
ufw delete allow/deny 20
```

### 1.3 代理

### 1.4 网络/IP

```
# 查看本机IP
ip addr show
```

## 2 软件源

```
sudo apt install xxx
sudo apt update
```

### 2.1 vsftpd

```
# 配置文件
/etc/vsftpd.conf

# 启动
sudo systemctl start/restart/stop vsftpd 
# sudo service vsftpd restart

# 如果用户是xxx，而不是root，那么需要先将目录的所有者设置为xxx
# 例子：根目录-查看权限、更改所有者、设置权限
ls -ld /
sudo chown xxx /
sudo chmod u+rwx /
```

## 99 三方库/服务

### 99.2 jdk

#### 99.2.1 jdk 1.8

```
sudo apt install openjdk-8-jdk
update-alternatives --list java

sudo vim ~/.bahsrc
# .bahsrc start
export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64
export JRE_HOME=$JAVA_HOME/jre
export CLASSPATH=.:$:CLASSPATH:$JAVA_HOME/lib
export PATH=$PATH:$JAVA_HOME/bin
# .bahsrc end

source ~/.bashrc # 生效
```