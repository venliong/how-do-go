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
        fmt.Printf("a = %d\n", a)
}

$go run test.go
a = 0
```



