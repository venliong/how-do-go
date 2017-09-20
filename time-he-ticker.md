## Timer和Ticker {#Timer和Ticker}

我们看一下关于时间的两个Channel。

timer是一个定时器，代表未来的一个单一事件，你可以告诉timer你要等待多长时间，它提供一个Channel，在将来的那个时间那个Channel提供了一个时间值。下面的例子中第二行会阻塞2秒钟左右的时间，直到时间到了才会继续执行。

```golang
timer1 := time.NewTimer(time.Second * 2)
<-timer1.C
fmt.Println("Timer 1 expired")
```

当然如果你只是想单纯的等待的话，可以使用`time.Sleep`来实现。

你还可以使用`timer.Stop`来停止计时器。

```golang
timer2 := time.NewTimer(time.Second)
go func() {
    <-timer2.C
    fmt.Println("Timer 2 expired")
}()
stop2 := timer2.Stop()
if stop2 {
    fmt.Println("Timer 2 stopped")
}
```

---

#### `ticker`

是一个定时触发的计时器，它会以一个间隔\(interval\)往Channel发送一个事件\(当前时间\)，而Channel的接收者可以以固定的时间间隔从Channel中读取事件。下面的例子中ticker每500毫秒触发一次，你可以观察输出的时间。

```golang
package main

import "fmt"
import "time"

func main() {
        ticker := time.NewTicker(time.Millisecond * 500)
        go func() {
                for t := range ticker.C {
                        fmt.Println("Tick at", t)
                }
        }()

        timer := time.NewTimer(time.Hour * 1)
        <-timer.C
}
```



