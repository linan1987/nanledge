# CentOS

## 1 系统

### 1.1 基础命令

```
# 查询当前系统版本
cat /etc/centos-release
```

### 1.2 防火墙

#### 常用命令

```
# 关闭防火墙(电脑重启会自动开启)
systemctl stop firewalld

# 彻底禁用防火墙(不会自动开启)
systemctl disable firewalld
```

### 1.3 端口

#### 1.3.1 常用命令

```
# 查看开启了哪些端口
netstat -tuln

# 查看端口占用
netstat -tuln | grep :80
```

#### 1.3.2 如果端口被selinux拦截，则需手动添加端口

SELinux 是一种 Linux 安全模块，用于限制进程的访问权限，以保护系统安全。  
这样可能会造成 nginx、node 等进程无法绑定端口。

```
# 查看状态
systemctl status nginx.service
journalctl -xe

# 方案一：将某个端口设置为 http 服务端口

semanage port -a -t http_port_t -p tcp 8809

# 方案二：将某个端口设置为普通端口

semanage port -a -t port_t -p tcp 8809
setsebool -P nis_enabled 1


# 重新启动，查看状态
systemctl start nginx
systemctl status nginx
```

### 1.4 代理

```
vim /etc/profile

export http_proxy=http://192.168.1.105:7890/
export https_proxy=https://192.168.1.105:7890/
export http_proxy
export https_proxy

source /etc/profile
```

### 1.5 修改ip地址

```
# 前提准备
路由做好静态ip设置
虚拟机网络设置成桥接

# 进入centos设置ip
vim /etc/sysconfig/network-scripts/ifcfg-ens33
--bootproto=none
--ipaddr=xxx.xxx.xxx.xxx
--gateway=xxx.xxx.xxx.xxx
--dns1=xxx.xxx.xxx.xxx

# 重启网络或重启虚拟机

# 查看ip是否生效
ifconfig
ping 宿主ip
```

## 2 软件源

### 2.1 yum

#### 2.1.1 常见命令

```shell
# 更新软件源
sudo yum update

# 下载某软件
sudo yum install xxx

# 卸载某软件
sudo yum remove xxx

# 启动/重启某个服务
sudo systemctl start/restart xxx
```

```shell
# centos 8+ 用 dnf 安装软件
dnf module list nodejs
dnf module install nodejs:20/common
```

#### 2.1.2 分类

```
# 客户端
客户端的配置非常简单，只要配置要一些基本的参数，就可以通过客户端来安装软件，并且解决软件包的依赖性。

# 服务端
将所有需要的软件包同统一放在一个目录下，该目录可以通过ftp、http、https、file将需要使用软件的客户端传输需要的软件。
```

#### 2.1.3 配置文件

```
# 全局配置(/etc/yum.conf)
cachedir：软件包缓存目录
keepcache：缓存是否保存，1保存0不保存
debuglevel：调试级别（默认为2）
logfile：日志文件路径
gpgcheck：是否检查密钥，一种检验软件完整性的方式

# 仓库配置(/etc/yum.repo.d/name.repo)
[name]：仓库id
name ：仓库名字
baseurl： 为仓库的地址
gpgkey：公钥地址，若是需要检查完整性的话可以添加密钥地址
enable：是否开启当前仓库
gpgcheck：是否使用密钥验证

# 仓库中的变量信息
releasever: 当前os的主版本号arch:处理器平台
basearch: 基础平台
```

#### 2.1.4 命令

```
# 启用与禁用仓库
禁用仓库:yum-config-manager --disable “仓库名"
启用仓库:yum-config-manager --enable “仓库名”

# 显示软件仓库列表
yum repolist

# 显示软件包列表
yum list

# 安装卸载与更新
安装：yum install package1 package2...
重新安装：yum reinstall package
卸载：yum remove package
更新：yum update package
降级：yum downgrage package
检查可用的更新：yum check-update

# 缓存命令
清除缓存：yum clean all
构建缓存：yum makecache

# 查看依赖性
yum deplist package1

# 包组相关命令
安装：yum groupinstall group1 [group2] [...]
更新yum groupupdate group1 [group2] [...]
列表yum grouplist [hidden] [groupwildcard] [...]
删除yum groupremove group1 [group2] [...]
信息yum groupinfo group1 [...]
```

#### 2.1.5 安装指定版本的软件

```
# 列出所有可用版本
yum list | grep <package_name>

# 查看特定软件包的所有可用版本
yum list --showduplicates <package_name>

# 安装
sudo yum install <package_name>-<version>

# 例如
sudo yum install httpd-2.4.6-90.el7.centos

请注意，你必须确保指定的版本在你的yum仓库配置中是可用的。如果版本不可用，yum将无法找到并安装它。
```

## 99 三方库/服务

