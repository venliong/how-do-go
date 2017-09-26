# 结构体

go 语言中数组可以存储同一类型的数据，但在结构体中我们可以为不同项定义不同的数据类型。

结构体是由一系列具有相同类型或不同类型的数据构成的数据集合。

结构体表示一项记录，比如保存图书馆的书籍记录，每本书有以下属性：

---

```golang
type struct_variable_type struct {
   member definition;
   member definition;
   ...
   member definition;
}
```

一旦定义了结构体类型，它就能用于变量的声明，语法格式如下：

```golang
variable_name := structure_variable_type {value1, value2...valuen}
```

---

## 访问结构体成员

如果要访问结构体成员，需要使用点号 \(.\) 操作符，格式为："结构体.成员名"。

结构体类型变量使用struct关键字定义，实例如下：

```golang
package main

import "fmt"

//定义结构体类型
type Books struct {
        title   string
        author  string
        subject string
        book_id int
}

func printBook(book Books) {
        fmt.Printf("Book title : %s\n", book.title)
        fmt.Printf("Book author: %s\n", book.author)
        fmt.Printf("Book subject : %s\n", book.subject)
        fmt.Printf("Book book_id : %d\n", book.book_id)
}

func main() {
        var book1 Books //声明book1位Books类型
        var book2 Books

        /* book1 的描述 */
        book1.title = "How do Go Lang"
        book1.author = "liudanbing"
        book1.subject = "go-itcast"
        book1.book_id = 100001

        /* book2 的描述 */
        book2.title = "Lua 上的linux应用"
        book2.author = "liudanbing"
        book2.subject = "lua"
        book2.book_id = 100002

        printBook(book1)

        printBook(book2)
}
```

结果为：

```golang
Book title : How do Go Lang
Book author: liudanbing
Book subject : go-itcast
Book book_id : 100001
Book title : Lua 上的linux应用
Book author: liudanbing
Book subject : lua
Book book_id : 100002
```

---

## 结构体指针

你可以定义指向结构体的指针类似于其他指针变量，格式如下：

```go
var struct_pointer *Books
```

以上定义的指针变量可以存储结构体变量的地址。查看结构体变量地址，可以将 & 符号放置于结构体变量前：

```go
struct_pointer =&Book1
```

使用结构体指针访问结构体成员，使用 "." 操作符：

```go
struct_pointer.title
```

接下来让我们使用结构体指针重写以上实例，代码如下：

```golang
package main

import "fmt"

//定义结构体类型
type Books struct {
        title   string
        author  string
        subject string
        book_id int
}

func printBook(book *Books) {
        fmt.Printf("Book title : %s\n", book.title)
        fmt.Printf("Book author: %s\n", book.author)
        fmt.Printf("Book subject : %s\n", book.subject)
        fmt.Printf("Book book_id : %d\n", book.book_id)
}

func main() {
        var book1 Books //声明book1位Books类型
        var book2 Books

        /* book1 的描述 */
        book1.title = "How do Go Lang"
        book1.author = "liudanbing"
        book1.subject = "go-itcast"
        book1.book_id = 100001

        /* book2 的描述 */
        book2.title = "Lua 上的linux应用"
        book2.author = "liudanbing"
        book2.subject = "lua"
        book2.book_id = 100002

        printBook(&book1)

        printBook(&book2)
}
```



