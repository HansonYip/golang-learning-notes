# 复数

复数类型：complex64 和 complex128，分别对应 float32 和 float64 两种浮点数精度。复数声明：

```go
var x = complex(3, 4)             // 3+4i，默认为 complex128
var y complex64 = complex(1, 2)   // 1+2i
z := 1 + 2i                       // 1+2i
```

内建的 real 和 imag 函数分别返回复数的实部和虚部：

```go
fmt.Println(real(x))           // 3
fmt.Println(imag(y))           // 2
```



