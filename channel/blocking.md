## blocking {#blocking}

缺省情况下，发送和接收会一直阻塞着，直到另一方准备好。这种方式可以用来在gororutine中进行同步，而不必使用显示的锁或者条件变量。

如官方的例子中`x, y := <-c, <-c`这句会一直等待计算结果发送到channel中。

```golang
package main

import "fmt"

func sum(s []int, c chan int) {
        sum := 0
        for _, v := range s {
                sum += v
        }
        c <- sum // send sum to c
}

func main() {
        s := []int{7, 2, 8, -9, 4, 0}
        c := make(chan int)

        go sum(s[len(s)/2:], c)
        go sum(s[:len(s)/2], c)

        x, y := <-c, <-c // receive from c
        fmt.Println(x, y, x+y)
}
```

结果

```golang
17 -5 12
```

---

## Buffered Channels {#Buffered_Channels}

ake的第二个参数指定缓存的大小：`ch := make(chan int, 100)`。

通过缓存的使用，可以尽量避免阻塞，提供应用的性能。  


---

## Range {#Range}

`for …… range`语句可以处理Channel。  


```golang
func main() {
	go func() {
		time.Sleep(1 * time.Hour)
	}()
	c := make(chan int)
	go func() {
		for i := 0; i < 10; i = i + 1 {
			c <- i
		}
		close(c)
	}()
	for i := range c {
		fmt.Println(i)
	}
	fmt.Println("Finished")
}
```

`range c`产生的迭代值为Channel中发送的值，它会一直迭代直到channel被关闭。上面的例子中如果把`close(c)`注释掉，程序会一直阻塞在`for …… range`那一行。

