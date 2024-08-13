---
title: Java数据类型
layout: doc
navbar: true
sidebar: true
aside: true
outline: deep
lastUpdated: true
editLink: true
footer: true
---

# 数据类型

Java中的数据类型分为:

- 基本数据类型: 包括`boolean`, `char`, `byte`, `short`, `int`, `long`, `float`, `double`
- 引用数据类型: 除了基本数据类型意外的类型, 都是引用类型, 常见的有数组, 类, 接口

## 变量

变量分为局部变量, 成员变量和静态变量.

::: tip
- 当变量是局部变量的时候, 必须初始化, 否则编译器编译不通过
- 当变量是成员变量或者静态变量的时候, 可以不进行初始化, 它们会有一个默认值
    | 数据类型 | 默认值   | 大小   |
    |----------|----------|--------|
    | boolean  | false    | 不确定 |
    | char     | '\u0000' | 2 字节 |
    | byte     | 0        | 1 字节 |
    | short    | 0        | 2 字节 |
    | int      | 0        | 4 字节 |
    | long     | 0L       | 8 字节 |
    | float    | 0.0f     | 4 字节 |
    | double   | 0.0      | 8 字节 |
:::

## 基本数据类型

### `boolean`

`boolean`类型只有两个值, `true`和`false`. 

在语言层面, Java没有明确规定`boolean`类型的大小. 具体的两种论调详见[这里](https://javabetter.cn/basic-grammar/basic-data-type.html#_1-布尔).

### `byte`

一个字节可以表示2^8=256个不同的值. 由于`byte`是有符号的, 它的值可以是负数或者正数, 其取值范围是-128到127. 在网络传输, 大文件读写时, 为了节省空间, 通常采用字节作为数据的传输方式.

### `int`

`int`的取值范围在-2^31和2^31-1(含)之间. 如果没有特殊要求, 整形数据就用`int`.

### `long`

`long`的取值范围在-2^63和2^63-1(含)之间. 如果`int`存储不下, 就用`long`.

### `float`

`float`是单精度浮点数, 有效数字大概6到7位. 遵循IEEE 754标准, 取值范围为1.4E-45到3.4E+38.

::: warning
为了和`double`做区分, `float`类型变量在声明的时候, 末尾要带上小写的`f`.
:::

### `double`

`double`是双精度浮点数, 有效数字大概15到17位. 遵循IEEE 754标准, 取值范围约+-4.9E-424到+-1.8E308. 

::: tip
IEEE 754标准具体内容请看[这里](https://javabetter.cn/basic-grammar/basic-data-type.html#_03%E3%80%81%E5%8D%95%E7%B2%BE%E5%BA%A6%E5%92%8C%E5%8F%8C%E7%B2%BE%E5%BA%A6).
:::

### `char`

`char`用于表示Unicode字符, 占16位, 取值范围为0到65535.

## 包装器类型

包装器类型, Wrapper Types是Java中的一种特殊类型, 用于将基本数据类型, 如`int`, `float`, `char`等转为对应的对象类型.

Java提供了以下包装器类型, 与基本数据类型一一对应:

| 包装器类型 | 基本数据类型 |
|------------|--------------|
| Byte       | byte         |
| Short      | short        |
| Integer    | int          |
| Long       | long         |
| Float      | float        |
| Double     | double       |
| Character  | char         |
| Boolean    | boolean      |

包装器类型允许我们使用基本数据类型提供的各种实用方法, 并兼容需要对象类型的场景. 

::: details EXAMPLE
下面是一个简单的实例, 演示了如何使用包装器类型:
```java
// 使用 Integer 包装器类型
Integer integerValue = new Integer(42);
System.out.println("整数值: " + integerValue);

// 将字符串转换为整数
String numberString = "123";
int parsedNumber = Integer.parseInt(numberString);
System.out.println("整数值: " + parsedNumber);

// 使用 Character 包装器类型
Character charValue = new Character('A');
System.out.println("字符: " + charValue);

// 检查字符是否为数字
char testChar = '9';
if (Character.isDigit(testChar)) {
System.out.println("字符是个数字.");
}
```
关于字符串转整数函数`parseInt()`的源码解释, 请看[这里](https://javabetter.cn/basic-grammar/basic-data-type.html#_05%E3%80%81%E5%8C%85%E8%A3%85%E5%99%A8%E7%B1%BB%E5%9E%8B).
:::

从Java5开始, 自动装箱和自动拆箱机制允许我们在基本数据类型和包装器类型之间自动转换, 无需显式地调用构造方法或者转换方法.

## 引用数据类型

引用数据类型与基本数据类型直接存储值不同, 它存储的是指向对象在内存中的位置的引用或者地址.

::: tip
引用数据类型也有默认值, 默认值是`null`.
:::

数组和接口也是引用数据类型.