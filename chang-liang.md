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

---

## 优雅的常量 iota

有些概念有名字，并且有时候我们关注这些名字，甚至（特别）是在我们代码中。

```golang
const (
    CCVisa            = "Visa"
    CCMasterCard      = "MasterCard"
    CCAmericanExpress = "American Express"
)
```

在其他时候，我们仅仅关注能把一个东西与其他的做区分。有些时候，有些时候一件事没有本质上的意义。比如，我们在一个数据库表中存储产品，我们可能不想以 string 存储他们的分类。我们不关注这个分类是怎样命名的，此外，该名字在市场上一直在变化。

我们仅仅关注它们是怎么彼此区分的。

```golang
const (
    CategoryBooks    = 0
    CategoryHealth   = 1
    CategoryClothing = 2
)
```

使用 0, 1, 和 2 代替，我们也可以选择 17， 43， 和 61。这些值是任意的。

在 Go，常量有许多微妙之处。当用好了，可以使得代码非常优雅且易维护的。

### 自增长

在 golang 中，一个方便的习惯就是使用`iota`标示符，它简化了常量用于增长数字的定义，给以上相同的值以准确的分类。

```golang
const (
    CategoryBooks = iota // 0
    CategoryHealth       // 1
    CategoryClothing     // 2
)
```

### 自定义类型

自增长常量经常包含一个自定义类型，允许你依靠编译器。

```golang
type Stereotype int //这是一个自定义类型 Stereotype 实际上就是 int类型

const (
    TypicalNoob Stereotype = iota // 0
    TypicalHipster                // 1
    TypicalUnixWizard             // 2
    TypicalStartupFounder         // 3
)
```

如果一个函数以`int`作为它的参数而不是`Stereotype`，如果你给它传递一个`Stereotype`，它将在编译器期出现问题。如下

```golang
package main

import "fmt"

type Stereotype int

const (
        TypicalNoob           Stereotype = iota // 0
        TypicalHipster                          // 1
        TypicalUnixWizard                       // 2
        TypicalStartupFounder                   // 3
)

/* -------------------------------------------*/
/**
* @brief  测试const形参匹配类型
*
* @param int
*
* @returns
*          string 类型
 */
/* -------------------------------------------*/
func CountAllTheThings(i int) string {
        //返回一个字符串 Sprintf是创建一个字符串
        return fmt.Sprintf("there are %d things", i)
}

func main() {

        n := TypicalHipster
        //虽然自定义类型,但是传参也是会报错...
        fmt.Println(CountAllTheThings(n))
}
```

```bash
output:
$cannot use TypicalHipster (type Stereotype) as type int in argument to CountAllTheThings
```

相反亦是成立的。给一个函数以`Stereotype`作为参数，你不能给它传递`int`。

```golang
func SoSayethThe(character Stereotype) string {
    var s string
    switch character {
    case TypicalNoob:
        s = "I'm a confused ninja rockstar."
    case TypicalHipster:
        s = "Everything was better we programmed uphill and barefoot in the snow on the SUTX 5918"
    case TypicalUnixWizard:
        s = "sudo grep awk sed %!#?!!1!"
    case TypicalStartupFounder:
        s = "exploit compelling convergence to syndicate geo-targeted solutions"
    }
    return s
}

func main() {
    i := 2
    fmt.Println(SoSayethThe(i))
}

// output:
// cannot use i (type int) as type Stereotype in argument to SoSayethThe
```

但是戏剧性的是，尽管如此，你可以传递一个数值常量，然后它却能够工作。

```golang
func main() {
    fmt.Println(SoSayethThe(0))
}

// output:
// I'm a confused ninja rockstar.
```

这是因为常量在 Go 中是弱类型直到它使用在一个严格的上下文环境中。



另外，我们可以使用下划线跳过不想要的值。



```golang
type AudioOutput int

const (
    OutMute AudioOutput = iota // 0
    OutMono                    // 1
    OutStereo                  // 2
    _
    _
    OutSurround                // 5
)

```

### iota和表达式



