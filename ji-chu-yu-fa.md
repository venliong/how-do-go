# 基础语法



## 分隔符



在 Go 程序中，一行代表一个语句结束。每个语句不需要像 C 家族中的其它语言一样以分号 ; 结尾，因为这些工作都将由 Go 编译器自动完成。

如果你打算将多个语句写在同一行，它们则必须使用 ; 人为区分，但在实际开发中我们并不鼓励这种做法。

以下为两个语句：

```golang
package main

import "fmt"

func main() {
        /* 简单的程序 万能的hello world */
        fmt.Println("Hello Go"); fmt.Println("hello go Again!")
}
```



所以我们应该建议每行只有一个表达式。







