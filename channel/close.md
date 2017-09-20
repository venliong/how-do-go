## Close



内建的close方法可以用来关闭channel。

总结一下channel关闭后sender的receiver操作。  
如果channel c已经被关闭,继续往它发送数据会导致`panic: send on closed channel`:



```golang
import "time"
func main() {
	go func() {
		time.Sleep(time.Hour)
	}()
	c := make(chan int, 10)
	c <- 1
	c <- 2
	close(c)
	c <- 3
}
```

但是从这个关闭的channel中不但可以读取出已发送的数据，还可以不断的读取零值:

```golang
c := make(chan int, 10)
c <- 1
c <- 2
close(c)
fmt.Println(<-c) //1
fmt.Println(<-c) //2
fmt.Println(<-c) //0
fmt.Println(<-c) //0
```



但是如果通过`range`读取，channel关闭后for循环会跳出：

