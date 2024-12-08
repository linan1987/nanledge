# Mysql

## 常用命令

```shell
# 首先登录mysql，进入MySQL命令行
mysql -u root -p

# 查看当前mysql版本
mysql -u root -p
```

## 卸载

```shell
# 方案一：Linux 通用方法

# 查看已安装的 mysql
rpm -qa|grep -i mysql

# 将上面给出的列表分别删除
rpm -ev xxx-a --nodeps
rpm -ev xxx-b --nodeps
rpm -ev xxx-c --nodeps

# 删除mysql相关目录
# /var/lib/mysql/ 必须删除
rm -rf /var/lib/mysql/
rm -rf /usr/lib64/mysql/
rm -rf /aaa/bbb/ccc/100/mysql/

# 删除相关配置文件
# 暂未验证是否必须删除
rm -rf /etc/my.cnf

# 查看卸载情况
# 显示为空，卸载完毕(但也未必)
rpm -qa|grep -i mysql

# 方案二：yum
# 该方法是否需要手动删除相关服务或文件，尚未了解
yum remove mysql
```

## 数据库迁移

```shell
【mysql数据迁移】
1 备份
# cd /opt/liuzi
mysqldump -u root -p liuzi > liuzi_xxx.sql

2 确认两边字符集一致，创建数据库
mysql -u root -p
    SHOW VARIABLES LIKE 'character_set_database';
    create database xxx;

4 恢复数据
mysql -u root -p example_db < /xxx/xxx.sql
```

## 阿里巴巴-建表规约

```
《阿里巴巴 Java 开发手册 1.4.0》的部分建表规约如下：

【强制】 表名、字段名必须使用小写字母或数字，禁止出现数字开头，禁止两个下划线中间只出现数字。
【强制】 主键索引名为pk_字段名；唯一索引名为uk_字段名；普通索引名则为idx_字段名。
【强制】 小数类型为 decimal，禁止使用 float 和 double。
【强制】 表必备三字段：id，create_time，update_time。其中 id 必为主键，类型为 bigint unsigned、单表自增、步长为 1。
```