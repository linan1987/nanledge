# Dart

## final

它是变量，不是常量。
只能被赋值一次。
如果一个类的属性是final，那么，在构造函数执行阶段就会被赋值，之后不能再修改。

## 函数
### 方法参数：必选和可选

```dart
// 必选
void hi(String name) {}
void hi({required String name}) {}
// 可选
void hi(String name, [int? age]) {}
void hi({String?.name}) {}
void hi({String.name = 'lilei'}) {}
```

## 类和对象

### 私有属性或方法 _

是指当前文件可访问，跨文件不可访问。

同一文件内，是可以调用的。
