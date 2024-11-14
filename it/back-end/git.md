# Git

> 注意：
> 
> （1）Git不再支持客户端用密码校验，改为ssh、personal token。  
> （2）macOS 配置ssh 多了一个步骤-ssh agent + config文件。或直接选择personal token的方式进行配置。
>  要复制ssh地址进行clone等操作。

## 1 代理

```
# 查看所有配置，包括代理
git config -l

# 设置代理
git config --global http.proxy 192.168.1.7:7890
git config --global https.proxy 192.168.1.7:7890
git config --global http.proxy socks5 192.168.1.7:7890
git config --global https.proxy socks5 192.168.1.7:7890

# 删除代理
git config --global --unset http.proxy
git config --global --unset https.proxy
git config --global --unset http.proxy socks5
git config --global --unset https.proxy socks5

# 如果提示：存在多个值
# 删除所有配置
git config --global --unset-all http.proxy
git config --global --unset-all https.proxy
git config --global --unset-all http.proxy socks5
git config --global --unset-all https.proxy socks5
```

## 2 设置鉴权缓存

> 类型分为：cache、store

### 2.1 cache

```
git config --global credential.helper cache

# timeout -> 秒
git config --global credential.helper 'cache --timeout=3600'
```

### 2.2 store

```
git config --global credential.helper store
```

## 3 用户设置

```
git config --global user.name "liuzi_admin"
git config --global user.email "admin@liuzi.online"
```

## 4 ssh配置

```
# 生产ssh密钥文件
ssh-keygen -t ed25519 -C "admin@liuzi.online"
```