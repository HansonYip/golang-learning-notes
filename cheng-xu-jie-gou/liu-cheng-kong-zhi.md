# 流程控制

## **for 循环**

Go语言的循环语句只有`for`循环，其一种形式如下：

```go
for initialization; condition; post {
    // zero or more statements
}
```

`for` 循环三个部分不需括号包围。左大括号必须和post语句在同一行。

`initialization`语句是可选的，在循环开始前执行。`initalization`如果存在，必须是一条简单语句（simple statement），即，短变量声明、自增语句、赋值语句或函数调用，**不可使用非短变量声明**`var`。

`condition`是一个布尔表达式（boolean expression），其值在每次循环迭代开始时计算。如果为 true 则执行循环体语句。

`post`语句在循环体执行结束后执行，之后再次对`conditon`求值。`condition`值为false时，循环结束。

for循环的这三个部分每个都可以省略，如下：

```go
for ;; {
    // do something 
}
```

甚至连分号也可以省略：

```go
for {
    // do something 
}
```

`for`循环的另一种形式`range`，常见如下两种：

```go
for i, value := range slice {
    // do something 
}

for key, value := range map {
    // do something 
}
```

每次循环迭代， `range`产生一对值，索引以及在该索引处的元素值，或者是键值对`(key, value)`。

## **if-else**

`if`是用于测试某个条件（布尔型或逻辑型）的语句，如果该条件成立，则会执行`if`后由大括号括起来的代码块。一般有以下几种形式：

```go
// 形式一
if condition {
    // do something 
}

// 形式二
if condition {
    // do something 
} else {
    // do something 
}

// 形式三
if condition1 {
    // do something 
} else if condition2 {
    // do something else    
} else {
    // catch-all or default
}

// 形式四
if initialization; condition {
    // do something
}
```

值得注意的是，形式四使用简短方式声明的变量的作用域只存在于`if`结构或`if-else`结构中。

## **switch**

Go语言中的switch结构使用上更加灵活，可接受任意形式的表达式：

```go
switch 变量 {
    case 表达式11[, 表达式12, ...]:
        ...
        [fallthrough]
    case 表达式21[, 表达式22, ...]:
        ...
        [fallthrough]
    case 表达式31[, 表达式32, ...]:
        ...
        [fallthrough]
    default:
        ...
}
```

变量可以是任何类型，而表达式则可以是同类型的任意值。每一个`case`分支都是唯一的，从上至下逐一测试，直到匹配为止。

一旦成功地匹配到某个分支，在执行完相应代码后就会退出整个`switch`代码块，也就是说您不需要特别使用`break`语句来表示结束。如果在执行完每个分支的代码后，还希望继续执行后续分支的代码，可以使用`fallthrough`关键字来达到目的。

当`switch`中省略被判断的变量时，则默认为判断`case`分支是否为`true`。

## **break、continue 与 goto**

Go语言中，`break`和`continue`的用法与Java基本一致，`break`用于`for`循环、`switch`和`select`中，作用是结束循环或当前整个代码块，而`continue`只能用于`for`循环，作用是忽略剩余的循环体而直接进入下一次循环的过程。

TODO：goto

