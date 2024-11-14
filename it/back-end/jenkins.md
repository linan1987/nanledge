# Jenkins

## 1 Linux 通用

## 2 Centos

## 3 Ubuntu

### 3.1 安装

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

### 3.2 启动

```
# service jenkins start
systemctl start/restart/stop jenkins
```

### 3.3 配置

```
sudo -s

vim /usr/lib/systemd/system/jenkins.service
# JENKINS_PORT  ->  端口号

systemctl daemon-reload
sudo systemctl restart jenkins
```

### 3.4 插件

### 3.4.1 镜像

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

### 3.4.2 角色插件

```
# 1 安装插件
Role-based Authorization StrategyVersion

# 2 全局安全配置
# 3 Manage and Assign Roles
```

### 3.4.3 凭证插件

```
Credentials
Trilead API
SSH Credentials
Credentials Binding
```

### 3.4.4 Git 插件

```
Git client
Instance Identity
Display URL API
Mailer
Git
```