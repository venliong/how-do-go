# 切片\(Slice\)



Go 语言切片是对数组的抽象。

Go 数组的长度不可改变，在特定场景中这样的集合就不太适用，Go中提供了一种灵活，功能强悍的内置类型切片_**`("动态数组")`**_,与数组相比切片的长度是不固定的，可以追加元素，在追加时可能使切片的容量增大。

---

## 定义切片

你可以声明一个未指定大小的数组来定义切片：

```golang
var identifier []type
```

切片不需要说明长度。

或使用make\(\)函数来创建切片:

```golang
var slice1 []type = make([]type, len)

也可以简写为

slice1 := make([]type, len)
```

也可以指定容量，其中capacity为可选参数。

```golang
make([]T, length, capacity)
```

这里 len 是数组的长度并且也是切片的初始长度。

---

### 切片初始化

```golang
s :=[] int {1,2,3 } 
```

直接初始化切片，\[\]表示是切片类型，{1,2,3}初始化值依次是1,2,3.其cap=len=3

```golang
s := arr[:] 
```

初始化切片s,是数组arr的引用

```golang
s := arr[startIndex:endIndex] 
```

将arr中从下标startIndex到endIndex-1 下的元素创建为一个新的切片

```golang
s := arr[startIndex:] 
```

缺省endIndex时将表示一直到arr的最后一个元素

```golang
s := arr[:endIndex] 
```

缺省startIndex时将表示从arr的第一个元素开始

```golang
s1 := s[startIndex:endIndex] 
```

通过切片s初始化切片s1

```golang
s :=make([]int,len,cap) 
```

通过内置函数make\(\)初始化切片s,\[\]int 标识为其元素类型为int的切片

---

## len\(\) 和 cap\(\) 函数

切片是可索引的，并且可以由 len\(\) 方法获取长度。

切片提供了计算容量的方法 cap\(\) 可以测量切片最长可以达到多少。

以下为具体实例：



```golang
package main

import "fmt"

func main() {
   var numbers = make([]int,3,5)

   printSlice(numbers)
}

func printSlice(x []int){
   fmt.Printf("len=%d cap=%d slice=%v\n",len(x),cap(x),x)
}
```

以上实例运行输出结果为:

```golang
len=3 cap=5 slice=[0 0 0]
```

---



