# iOS 开发中遇到的问题

## Xcode 连接真机提示 is not available because it is unpaired

#### 描述

iPhone 15 is not availablebecause it is unpaired，Pair with the device in the XcodeDevices Window, and respond to anypairing prompts on the device.

#### 解决方法

1、退出XCode,断开设备连接

2、在终端执行

```
sudo pkill usbmuxd
```

4、重新打开xcode连接手机问题解决

## Xcode 构建发包时提示 framework 包含 bitcode

#### 描述

Invalid Executable. The excecutable "...app/Frameworks/hermes.framework/hermes" contains bitcode.

#### 解决方法

1、找到构建的 app 包文件，右键 - 显示包内容。

2、在 Frameworks 目录下，执行命令：

```
xcrun bitcode_strip -r hermes.framework/hermes -o hermes.framework/hermes
```

## SDK "iphoneos" cannot be located

很可能是由于电脑里有多个版本的 Xcode

#### 解决方法

1、确认 Xcode 已经安装了模拟器。

2、确认 sdk 路径正确

```
# 打印 sdk 路径
xcrun --sdk iphoneos --show-sdk-path

# 打印 Xcode 路径
xcode-select --print-path
xcodebuild -showsdks

# 设置正确的路径(把后面的路径替换成你认为正确的)
sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer/

# 检查 sdk 路径是否正确
xcrun --sdk iphoneos --show-sdk-path
```

3、重启 Xcode。