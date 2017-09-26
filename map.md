# Map\(集合\)

Map 是一种无序的键值对的集合。Map 最重要的一点是通过 key 来快速检索数据，key 类似于索引，指向数据的值。

Map 是一种集合，所以我们可以像迭代数组和切片那样迭代它。不过，Map 是无序的，我们无法决定它的返回顺序，这是因为 Map 是使用 hash 表来实现的。

### 定义 Map

可以使用内建函数 make 也可以使用 map 关键字来定义 Map:

```golang
/* 声明变量，默认 map 是 nil */
var map_variable map[key_data_type]value_data_type

/* 使用 make 函数 */
map_variable := make(map[key_data_type]value_data_type)
```

如果不初始化 map，那么就会创建一个 nil map。nil map 不能用来存放键值对

### 实例

下面实例演示了创建和使用map:

```golang
package main

import "fmt"

func main() {

        /* 定义map集合 */
        //声明map类型集合
        var countryCapitalMap map[string]string
        //给map集合开辟空间
        countryCapitalMap = make(map[string]string)

        /*  赋值 */
        countryCapitalMap["France"] = "Paris"
        countryCapitalMap["Italy"] = "Rome"
        countryCapitalMap["Japan"] = "Tokyo"
        countryCapitalMap["China"] = "Beijing"

        /* 使用key 输出map的值 */
        for country := range countryCapitalMap {
                fmt.Println("Capital of", country, "is", countryCapitalMap[country])
        }

        capital, ok := countryCapitalMap["USA"]
        if ok {
                fmt.Println("Capital of USA is ", capital)
        } else {
                fmt.Println("Capital of USA is not present")
        }

}

```

以上实例运行结果为：

```golang
Capital of France is Paris
Capital of Italy is Rome
Capital of Japan is Tokyo
Capital of China is Beijing
Capital of USA is not present
```

---

## delete\(\) 函数

delete\(\) 函数用于删除集合的元素, 参数为 map 和其对应的 key。实例如下：

```golang
package main

import "fmt"

func main() {   
   /* 创建 map */
   countryCapitalMap := map[string] string {"France":"Paris","Italy":"Rome","Japan":"Tokyo","India":"New Delhi"}
   
   fmt.Println("原始 map")   
   
   /* 打印 map */
   for country := range countryCapitalMap {
      fmt.Println("Capital of",country,"is",countryCapitalMap[country])
   }
   
   /* 删除元素 */
   delete(countryCapitalMap,"France");
   fmt.Println("Entry for France is deleted")  
   
   fmt.Println("删除元素后 map")   
   
   /* 打印 map */
   for country := range countryCapitalMap {
      fmt.Println("Capital of",country,"is",countryCapitalMap[country])
   }
}
```



