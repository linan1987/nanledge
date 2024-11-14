# JDK

## 1 Linux 通用

```
```

## 2 Centos

## 3 Ubuntu

### 3.1 jdk 1.8

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