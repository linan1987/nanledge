# 手机通过PC热点访问PC虚拟机

1、控制面板-网络和Internet-网络和共享中心-更改适配器设置：

VMnet1：vmware仅主机模式对应的虚拟网卡

VMnet8：vmware NAT模式对应的虚拟网卡

WLAN：wifi

本地连接*10：热点

以太网：有线网（连接的网线）

2、右键VMnet8-属性-共享：

3、开启共享，专用网络连接选择本地连接*10（热点），点击确定

确定后VMnet8的状态：

4、局域网电脑c连接热点，可以ping通192.168.200.100了。