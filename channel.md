# Go Channel 详解

Channel是Go中的一个核心类型，你可以把它看成一个管道，通过它并发核心单元就可以发送或者接收数据进行通讯\(communication\)。

它的操作符是箭头`<-`。

```golang
ch <- v    // 发送值v到Channel ch中
v := <-ch  // 从Channel ch中接收数据，并将数据赋值给v
```

\(箭头的指向就是数据的流向\)

就像 map 和 slice 数据类型一样, channel必须先创建再使用:

```golang
ch := make(chan int)
```

---

## Channel类型 {#Channel类型}

Channel类型的定义格式如下：

```golang
ChannelType = ( "chan" | "chan" "<-" | "<-" "chan" ) ElementType
```

它包括三种类型的定义。可选的`<-`代表channel的方向。如果没有指定方向，那么Channel就是双向的，既可以接收数据，也可以发送数据。

```golang
chan T          // 可以接收和发送类型为 T 的数据
chan<- float64  // 只可以用来发送 float64 类型的数据
<-chan int      // 只可以用来接收 int 类型的数据
```

`<-`总是优先和最左边的类型结合。

```golang
chan<- chan int    // 等价 chan<- (chan int)
chan<- <-chan int  // 等价 chan<- (<-chan int)
<-chan <-chan int  // 等价 <-chan (<-chan int)
chan (<-chan int)
```

使用`make`初始化Channel,并且可以设置容量:

```golang
make(chan int, 100)
```

容量\(capacity\)代表Channel容纳的最多的元素的数量，代表Channel的缓存的大小。  
如果没有设置容量，或者容量设置为0, 说明Channel没有缓存，只有sender和receiver都准备好了后它们的通讯\(communication\)才会发生\(Blocking\)。如果设置了缓存，就有可能不发生阻塞， 只有buffer满了后 send才会阻塞， 而只有缓存空了后receive才会阻塞。一个nil channel不会通信。

可以通过内建的`close`方法可以关闭Channel。

> 你可以在多个goroutine 从/往 一个channel 中 receive/send 数据, 不必考虑额外的同步措施。

Channel可以作为一个先入先出\(FIFO\)的队列，接收的数据和发送的数据的顺序是一致的。

channel的 receive支持_multi-valued assignment（多值赋值）_，如

```golang
v, ok := <-ch
```

它可以用来检查Channel是否已经被关闭了.

---

### **send语句**

send语句用来往Channel中发送数据， 如`ch <- 3`。

它的定义如下:

```golang
SendStmt = Channel "<-" Expression 
Channel  = Expression
```

在通讯\(communication\)开始前channel和expression必选先求值出来\(evaluated\)，比如下面的\(3+4\)先计算出7然后再发送给channel。

```golang
package main

import (
        "fmt"
        "time"
)

func main() {
        c := make(chan int)
        defer close(c)

        //开启一个子goroutine
        go func() {
                c <- 3 + 4
                fmt.Println("send 7 to c end.")
        }()

        time.Sleep(3 * time.Second)
        i := <-c
        fmt.Printf("i = %d\n ", i)
        fmt.Printf("main end. ")
}
```

send被执行前\(proceed\)通讯\(communication\)一直被阻塞着。如前所言，无缓存的channel只有在receiver准备好后send才被执行。如果有缓存，并且缓存未满，则send会被执行。

* _往一个已经被close的channel中继续发送数据会导致**run-time panic**。_
* _往nil channel中发送数据会一致被阻塞着。_

---

### receive 语句

`<-ch`用来从channel ch中接收数据，这个表达式会一直被block,直到有数据可以接收。

* _从一个nil channel中接收数据会一直被block。_

* _从一个被close的channel中接收数据不会被阻塞，而是立即返回，接收完已发送的数据后会返回元素类型的零值\(zero value\)。_

如前所述，你可以使用一个额外的返回参数来检查channel是否关闭。

```golang
x, ok := <-ch
x, ok = <-ch
var x, ok = <-ch
```

如果OK 是false，表明接收的x是产生的零值，这个channel被关闭了或者为空。

