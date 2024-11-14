# React Native 开发中遇到的问题

## 多个 Modal 组件在 iOS 端无法展示

#### 描述

举例：在 iOS 端，先展示一个 modal，再展示第二个 modal，第二个不显示。只有把第一个关了，第二个才展示。  
在 android 端是正常的。

#### 解决方法

iOS 在屏幕上只允许展示一个 modal 组件，所以：

方案一：  
在展示第二个 modal 前，关闭第一个 modal，达到切换展示的效果。

方案二：  
使用第三方库 `react-native-root-siblings‌`, `‌react-native-root-modal‌`。

## No bundle URL present

#### 解决方法

取消代理设置