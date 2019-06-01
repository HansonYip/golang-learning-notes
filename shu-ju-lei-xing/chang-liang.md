# 常量

常量值必须是编译期可确定的数字、字符串、布尔值。声明后，常量不可改。

```go
const a, b = 1, 2
```

所有常量的运算都可以在编译期完成，包括一下函数调用：len、cap、real、imag、complex和unsafe.Sizeof 。

```go
const a, b int = 1, 2
```

如果没有显式指明类型，那么将从右边的表达式推断类型，也称为[无类型常量](chang-liang.md#wu-lei-xing-chang-liang)。

```go
const (
    a = 1
    b
    c = 2
    d
)
fmt.Println(a, b, c, d) // "1 1 2 2"
```

在常量组中，如不提供类型和初始化值，那么视作与上⼀一常量相同。

## 无类型常量

无类型的常量类型共六种：

* 无类型的布尔型
* 无类型的整数
* 无类型的字符
* 无类型的浮点数
* 无类型的复数
* 无类型的字符串

```go
const a = 1          // untyped integer
const b = 1.1        // untyped fload-point
const c = true       // untyped bool
```

无类型常量具备更高数据精度。

```go
const a = 10000000000000000000      // 超过 int64 的最大值
const b = a / 100000
var c int64 = a                     // 异常：overflows int64
```

不同类型的无类型常量运算，不需要显性[类型转换](lei-xing-zhuan-huan.md)。

```go
const a = 1            // untyped integer
const b = 1.0          // untyped float-point
fmt.Println(a * b)     // a: untyped integer -> untyped float-point
```

无类型的常量被赋值给一个变量的时候，无类型的常量将会被隐式转换为对应的类型。

```go
var f float64 = 3 + 0i // untyped complex -> float64
f = 2                  // untyped integer -> float64
f = 1e123              // untyped floating-point -> float64
f = 'a'                // untyped rune -> float64
```

## **枚举（iota）**

关键字 iota 定义常量组中从 0 开始按行计数的自增枚举值。

```go
const (
    Sunday = iota    // 0
    Monday           // 1，通常省略后续⾏行表达式。
    Tuesday          // 2
    Wednesday        // 3
    Thursday         // 4
    Friday           // 5
    Saturday         // 6
)

const (
    _        = iota               // iota = 0
    KB int64 = 1 << (10 * iota)   // iota=1
    MB                            // 与 KB 表达式相同，但 iota = 2
    GB
    TB
)
```

在同⼀常量组中，可以提供多个 iota，它们各自增⻓。

```go
const (
    A, B = iota, iota << 10     // 0, 0 << 10
    C, D                       // 1, 1 << 10
)
```

如果 iota ⾃增被打断，须显式恢复。

```go
const (
    A = iota    // 0
    B           // 1
    C = "c"     // c
    D           // c
    E = iota    // 4，显式恢复，注意计数包含了 C、D 两⾏。
    F           // 5
)
```

可通过自定义类型来实现枚举。

```go
type Animal int

const(
    Dog Animal = iota
    Cat
    Snake
)
```

