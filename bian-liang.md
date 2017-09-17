# 变量

声明变量的一般形式是使用 var 关键字

### 变量声明

第一种，指定变量类型，声明后若不赋值，使用默认值0。

```golang
var v_name v_type
v_name = value
```

```golang
package main

import "fmt"

func main() {
        var a int
        fmt.Printf(" = %d\n", a)
}

$go run test.go
a = 0
```

第二种，根据值自行判定变量类型。

```golang
var v_name = value
```

第三种，省略var, 注意 :=左侧的变量不应该是已经声明过的，否则会导致编译错误。

```golang
v_name := value

// 例如
var a int = 10
var b = 10
c : = 10
```

例如：

```golang
package main

import "fmt"

func main() {
        //第一种 使用默认值
        var a int
        fmt.Printf("a = %d\n", a)

        //第二种
        var b int = 10
        fmt.Printf("b = %d\n", b)

        //第三种 省略后面的数据类型,自动匹配类型
        var c = 20
        fmt.Printf("c = %d\n", c)

        //第四种 省略var关键字
        d := 3.14
        fmt.Printf("d = %f\n", d)
}
```

---

### 多变量声明

```golang
package main

import "fmt"

var x, y int
var ( //这种分解的写法,一般用于声明全局变量
        a int
        b bool
)

var c, d int = 1, 2
var e, f = 123, "liudanbing"

//这种不带声明格式的只能在函数体内声明
//g, h := 123, "需要在func函数体内实现"

func main() {
        g, h := 123, "需要在func函数体内实现"
        fmt.Println(x, y, a, b, c, d, e, f, g, h)
}
```

---

### 值类型和引用类型

所有像 int、float、bool 和 string 这些基本类型都属于值类型，使用这些类型的变量直接指向存在内存中的值：



![](/assets/go4.png)



当使用等号`=`将一个变量的值赋值给另一个变量时，如：`j = i`，实际上是在内存中将 i 的值进行了拷贝：

![](/assets/go5.png)



你可以通过 &i 来获取变量 i 的内存地址，例如：0xf840000040（每次的地址都可能不一样）。值类型的变量的值存储在栈中。

