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

##  {#Channel类型}



