# Linux 通用

## 1 系统

### 1.1 基础命令

```shell
# 卸载

# 查看已安装的 xxx
rpm -qa|grep -i xxx

# 将上面给出的列表分别删除
rpm -ev xxx-a --nodeps
rpm -ev xxx-b --nodeps
rpm -ev xxx-c --nodeps

# 删除mysql相关目录
find / -name xxx
rm -rf /a/b/xxx/
rm -rf /c/d/xxx/
例如：rm -rf /var/lib/mysql/，rm -rf /usr/lib64/mysql

# 删除相关配置文件
例如：rm -rf /etc/my.cnf

# 查看卸载情况(显示为空，卸载完毕。)
rpm -qa|grep -i xxx
```

### 1.2 防火墙

### 1.3 代理

### 1.4 网络/IP

## 2 软件源

### 2.1 vim

```
i # 插入/修改文本
esc # 退出编辑状态
:wq # 保存并退出
:q! # 退出，不保存
```

## 99 三方库/服务

