## Go 语言变量作用域

  
作用域为已声明标识符所表示的常量、类型、变量、函数或包在源代码中的作用范围。

Go 语言中变量可以在三个地方声明：

* 函数内定义的变量称为局部变量
* 函数外定义的变量称为全局变量
* 函数定义中的变量称为形式参数

接下来让我们具体了解局部变量、全局变量和形式参数。

---

## 局部变量

在函数体内声明的变量称之为局部变量，它们的作用域只在函数体内，参数和返回值变量也是局部变量。

以下实例中 main\(\) 函数使用了局部变量 a, b, c：



```golang
package main

import "fmt"

func main() {
   /* 声明局部变量 */
   var a, b, c int 

   /* 初始化参数 */
   a = 10
   b = 20
   c = a + b

   fmt.Printf ("结果： a = %d, b = %d and c = %d\n", a, b, c)
}

```

以上实例执行输出结果为：


