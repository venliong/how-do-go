# 数据类型

---

在 Go 编程语言中，数据类型用于声明函数和变量。

数据类型的出现是为了把数据分成所需内存大小不同的数据，编程的时候需要用大数据的时候才需要申请大内存，就可以充分利用内存。

Go 语言按类别有以下几种数据类型：



**布尔型**

布尔型的值只可以是常量 true 或者 false。一个简单的例子：

```golang
var b bool = true。
```

**整型**

整型 int 和浮点型 float，Go 语言支持整型和浮点型数字，并且原生支持复数，其中位的运算采用补码。



**字符串类型:**

字符串就是一串固定长度的字符连接起来的字符序列。Go的字符串是由单个字节连接起来的。Go语言的字符串的字节使用UTF-8编码标识Unicode文本。



**派生类型:**

包括：

* \(a\) 指针类型（Pointer）
* \(b\) 数组类型
* \(c\) 结构化类型\(struct\)
* \(d\) Channel 类型
* \(e\) 函数类型
* \(f\) 切片类型
* \(g\) 接口类型（interface）
* \(h\) Map 类型

---

## 整型

Go 也有基于架构的类型，例如：int、uint 和 uintptr。

**uint8**

无符号 8 位整型 \(0 到 255\)

**uint16**

无符号 16 位整型 \(0 到 65535\)

**uint32**

无符号 32 位整型 \(0 到 4294967295\)

**uint64**

无符号 64 位整型 \(0 到 18446744073709551615\)

**int8**

有符号 8 位整型 \(-128 到 127\)

**int16**

有符号 16 位整型 \(-32768 到 32767\)

**int64**

有符号 64 位整型 \(-9223372036854775808 到 9223372036854775807\)

> #### 常用整型

**byte**

类似 uint8

**rune**

类似 int32

**uint**

32 或 64 位

**int**

与 uint 一样大小

**uintptr**

无符号整型，用于存放一个指针

---

### 浮点型：

### 

**float32**

IEEE-754 32位浮点型数

  
**float64**

IEEE-754 64位浮点型数



**complex64**

32 位实数和虚数



**complex128**

64 位实数和虚数

---



查看一个变量的数据类型

```golang
package main

import (
        "fmt"
        "reflect"
)

func main() {

        var x float64 = 3.4
        var y string = "abc"
        var a uint8 = 10
        var b uint16 = 10
        var c int = 100

        fmt.Println("x's type:", reflect.TypeOf(x))
        fmt.Println("y's type:", reflect.TypeOf(y))
        fmt.Println("a's type:", reflect.TypeOf(a))
        fmt.Println("b's type:", reflect.TypeOf(b))
        fmt.Println("c's type:", reflect.TypeOf(c))
}
```













