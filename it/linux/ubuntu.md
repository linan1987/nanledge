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

### 99.3 Jenkins

#### 99.3.1 安装

```
# https://pkg.jenkins.io/debian-stable/

#
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
    /usr/share/keyrings/jenkins-keyring.asc > /dev/null

#
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
    https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
    /etc/apt/sources.list.d/jenkins.list > /dev/null

#
sudo apt-get update
sudo apt-get install fontconfig
sudo apt-get install openjdk-8-jre # 可选

#
sudo apt install jenkins=2.346.1 #对应java 8

# 安装完后，Jenkins会自动启动
systemctl enable jenkins
```

#### 99.3.2 启动

```
# service jenkins start
systemctl start/restart/stop jenkins
```

#### 99.3.3 配置

```
sudo -s

vim /usr/lib/systemd/system/jenkins.service
# JENKINS_PORT  ->  端口号

systemctl daemon-reload
sudo systemctl restart jenkins
```

#### 99.3.4 插件

#### 99.3.4.1 镜像

```
# 官方镜像
https://updates.jenkins.io/update-center.json

#
sudo -s
cd /var/lib/jenkins/updates

# 修改国内镜像
sed -i 's/http:\/\/updates.jenkins-ci.org\/download/https:\/\/mirrors.tuna.tsinghua.edu.cn\/jenkins/g' default.json && sed -i 's/http:\/\/www.google.com/https:\/\/www.baidu.com/g' default.json

# 插件列表，带版本号
# https://updates.jenkins-ci.org/download/plugins/
```

#### 99.3.4.2 角色插件

```
# 1 安装插件
Role-based Authorization StrategyVersion

# 2 全局安全配置
# 3 Manage and Assign Roles
```

#### 99.3.4.3 凭证插件

```
Credentials
Trilead API
SSH Credentials
Credentials Binding
```

#### 99.3.4.4 Git 插件

```
Git client
Instance Identity
Display URL API
Mailer
Git
```