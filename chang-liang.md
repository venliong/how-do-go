# 常量

常量是一个简单值的标识符，在程序运行时，不会被修改的量。

常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型。

常量的定义格式：

```golang
const identifier [type] = value
```

你可以省略类型说明符 \[type\]，因为编译器可以根据变量的值来推断其类型。

* 显式类型定义：

```golang
const b string = "abc"
```

* 隐式类型定义：

```golang
const b = "abc"
```

例如：

```golang
package main

import "fmt"

func main() {
   const LENGTH int = 10
   const WIDTH int = 5   
   var area int
   const a, b, c = 1, false, "str" //多重赋值

   area = LENGTH * WIDTH
   fmt.Printf("面积为 : %d\n", area)
   println(a, b, c)   
}
```

以上实例运行结果为：

```golang
面积为 : 50
1 false str
```

常量还可以用作枚举：

```golang
const (
    Unknown = 0
    Female = 1
    Male = 2
)
```

数字 0、1 和 2 分别代表未知性别、女性和男性。

常量可以用len\(\), cap\(\), unsafe.Sizeof\(\)常量计算表达式的值。常量表达式中，函数必须是内置函数，否则编译不过：

```golang
package main

import "unsafe"
const (
    a = "abc"
    b = len(a)
    c = unsafe.Sizeof(a)
)

func main(){
    println(a, b, c)
}
```

输出结果为：abc, 3, 16



> unsafe.Sizeof\(a\)输出的结果是16 。
>
> 字符串类型在 go 里是个结构, 包含指向底层数组的指针和长度,这两部分每部分都是 8 个字节，所以字符串类型大小为 16 个字节。





