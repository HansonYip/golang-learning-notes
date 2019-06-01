# 命名

#### 命名

Go语言中的函数名、变量名、常量名、类型名、语句标号和包名等所有的命名，都遵循一个简单的命名规则：一个名字必须以一个字母（Unicode字母）或下划线开头，后面可以跟任意数量的字母、数字或下划线。一般推荐使用**驼峰式**命名。

Go语言中，关键字共25个：

```text
break      default       func     interface   select
case       defer         go       map         struct
chan       else          goto     package     switch
const      fallthrough   if       range       type
continue   for           import   return      var
```

此外，预留名字约30个分别是

* 内建常量

  ```text
  true    false   iota    nil
  ```

* 内建类型

  ```text
  int        int8       int16        int32     int64
  uint       uint8      uint16       uint32    uint64    uintptr
  bool       byte       rune         string    error
  float32    float64    complex128   complex64
  ```

* 内建函数

  ```text
  make       len     cap     new      append     copy    close
  complex    real    imag    panic    recover    delete
  ```

  预留名字并不是关键字，你可以再定义中重新使用它们。

名字的开头字母的大小写决定了名字在包外的可见性。如果一个名字是大写字母开头的（必须是包级名字），那么它将是导出的，也就是说可以被外部的包访问。

