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

  


