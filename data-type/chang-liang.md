# 常量

常量值必须是编译期可确定的数字、字符串、布尔值。声明后，常量不可改。

```go
const a, b = 1, 2       // 形式一
```

所有常量的运算都可以在编译期完成，包括一下函数调用：len、cap、real、imag、complex和unsafe.Sizeof 。

```go
const a, b int = 1, 2   // 形式二
```

如果没有显式指明类型，那么将从右边的表达式推断类型。

```go
const (     // 形式三
    a = 1
    b
    c = 2
    d
)
fmt.Println(a, b, c, d) // "1 1 2 2"
```

在常量组中，如不提供类型和初始化值，那么视作与上⼀一常量相同。

## **枚举（iota）**

关键字 iota 定义常量组中从 0 开始按行计数的自增枚举值。

```go
const (
    Sunday = iota    // 0
    Monday          // 1，通常省略后续⾏行表达式。
    Tuesday         // 2
    Wednesday       // 3
    Thursday        // 4
    Friday          // 5
    Saturday        // 6
)

const (
    _        = iota               // iota = 0
    KB int64 = 1 << (10 * iota)   // iota=1
    MB                          // 与 KB 表达式相同，但 iota = 2
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

