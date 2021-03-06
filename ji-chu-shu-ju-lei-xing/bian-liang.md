# 变量

变量声明的语法如下：

```go
var 变量名字[, 变量名字2, 变量名字3, ...] 类型                               // 形式一
var 变量名字[, 变量名字2, 变量名字3, ...] = 表达式[, 表达式2, 表达式3, ...]       // 形式二
var 变量名字[, 变量名字2, 变量名字3, ...] 类型 = 表达式[, 表达式2, 表达式3, ...]   // 形式三
```

* 形式一，采用与类型相对应的零值初始化该变量，零值初始化机制可以确保每个声明的变量总是有一个良好定义的值，不同类型的零值如下：

| 类型 | 零值 |
| :--- | :--- |
| 数值类 | 0 |
| bool | false |
| string | 空字符串（""） |
| 引用类型（slice、map、chan） | nil |
| 指针 | nil |
| 函数 | nil |
| 接口 | nil |
| 数组、结构体 | 每个元素或字段都是对应该类型的零值 |

* 形式二，将根据初始化表达式来推导变量的类型信息, 可定义不同类型的变量；
* 形式三，当变量类型与初值类型相同时，类型冗余，但如果两者类型不同，可显性指定变量类型。

## **简短变量**

简短变量声明语句的形式可用于声明和初始化局部变量，只能用在函数内部，而不能用于包级变量。变量的类型根据表达式来自动推导，与上述的形式二相似，声明方式如下：

```go
变量名字[, 变量名字2, 变量名字3, ...] := 表达式[, 表达式2, 表达式3, ...]
```

* 简短变量声明语句中必须至少要声明一个新的变量；
* 如果有一些已经在相同的词法域声明过了，声明语句对这些已经声明过的变量就只有赋值行为了；
* 简短变量声明语句只有对已经在同级词法域声明过的变量才和赋值操作语句等价；
* 如果变量是在外部词法域声明的，那么简短变量声明语句将会在当前词法域重新声明一个新的变量。

## **指针**

一个指针可以指向任何一个值的内存地址，它指向那个值的内存地址。指针式一种特殊的变量，储存的不止普通值，而是值的内存地址，甚至可以是另一个指针的地址，即指针的指针。

指针本质也是一种变量，声明方式与普通变量声明方式一致，指针声明格式如下：

```go
var 指针名字[, 指针名字2, ...] *类型
var 指针名字[, 指针名字2, ...] = 表达式[, 表达式2, ...]
var 指针名字[, 指针名字2, ...] *类型 = 表达式[, 表达式2, ...]

指针名字[, 指针名字2, ...] := 表达式[, 表达式2, ...]
```

常见的表达式如下：

```go
// 取址操作符
指针名字[, 指针名字2, ...] := &变量名[, 变量名2, ...]

// new函数
指针名字[, 指针名字2, ...] := new(类型)[, new(类型2), ...]
```

`&x` 表达式（取 x 变量的内存地址）将产生一个指向该整数变量的指针。

表达式`new(T)`将创建一个T类型的匿名变量，初始化为T类型的零值，然后返回变量地址，返回的指针类型为`*T`。

此外，`*x`表达式读取指针指向的变量的值，式也可以出现在赋值语句的左边，表示更新指针所指向的变量的值。

因为指针包含了一个变量的地址，因此如果将指针作为参数调用函数，那将可以在函数中通过该指针来更新变量的值。

## **变量的生命周期**

变量的生命周期指的是在程序运行期间变量有效存在的时间间隔。对于在包一级声明的变量来说，它们的生命周期和整个程序的运行周期是一致的。

而相比之下，在局部变量的声明周期则是动态的：从每次创建一个新变量的声明语句开始，直到该变量不再被引用为止，然后变量的存储空间可能被回收。

## **赋值**

赋值语句格式如下；

```go
变量[, 变量2, ...] = 表达式[, 表达式2, ...]
```

赋值语句是显式的赋值形式，但是程序中还有很多地方会发生隐式的赋值行为：函数调用会隐式地将调用参数的值赋值给函数的参数变量，一个返回语句将隐式地将返回操作的值赋值给结果变量。

