# Objective-C笔记

## 数据类型与C语言的区别

```
1.
OC支持C语言当中所有类型：
int, double, float, char,
array, struct, enum,
pointer,
void(空类型),
typedef(自定义类型).

2.
新增了如下类型：
BOOL,
Boolean(本质是BOOL，好像不常用),
class, id, nil, SEL, block,

3.
nil与NULL本质没有区别，分别应用在oc和c中。
```

## 异常捕获

```
1.
oc中的try/catch无法捕获c语言中的异常。
一般比较少用。
还是要多用if判断降低异常出现概率。
```

## 类与对象
```
类方法不能访问属性、对象方法。
对象方法可以访问类方法。
```