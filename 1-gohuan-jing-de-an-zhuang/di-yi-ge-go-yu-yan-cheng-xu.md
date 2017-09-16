# 第一个Go语言程序

# 

```go
package main

import "fmt"

func main() {
        /* 简单的程序 万能的hello world */
        fmt.Println("Hello Go")
}
```



终端运行

```go
$ go run test1_hello.go 
Hello Go
$
```

go run 表示 直接编译go语言并执行应用程序，一步完成



你也可以先编译，然后再执行

```bash
 $go build test1_hello.go 
 $./test1_hello
 Hello Go
```





