# 运算符

运算符用于在程序运行时执行数学或逻辑运算。

Go 语言内置的运算符有：

* 算术运算符
* 关系运算符
* 逻辑运算符
* 位运算符
* 赋值运算符
* 其他运算符

接下来让我们来详细看看各个运算符的介绍。

---

## 算术运算符

下表列出了所有Go语言的算术运算符。假定 A 值为 10，B 值为 20。

| 运算符 | 描述 | 实例 |
| :--- | :--- | :--- |
| + | 相加 | A + B 输出结果 30 |
| - | 相减 | A - B 输出结果 -10 |
| \* | 相乘 | A \* B 输出结果 200 |
| / | 相除 | B / A 输出结果 2 |
| % | 求余 | B % A 输出结果 0 |
| ++ | 自增 | A++ 输出结果 11 |
| -- | 自减 | A-- 输出结果 9 |

以下实例演示了各个算术运算符的用法：



```golang
package main

import "fmt"

func main() {

   var a int = 21
   var b int = 10
   var c int

   c = a + b
   fmt.Printf("第一行 - c 的值为 %d\n", c )
   c = a - b
   fmt.Printf("第二行 - c 的值为 %d\n", c )
   c = a * b
   fmt.Printf("第三行 - c 的值为 %d\n", c )
   c = a / b
   fmt.Printf("第四行 - c 的值为 %d\n", c )
   c = a % b
   fmt.Printf("第五行 - c 的值为 %d\n", c )
   a++
   fmt.Printf("第六行 - c 的值为 %d\n", a )
   a--
   fmt.Printf("第七行 - c 的值为 %d\n", a )
}
```

以上实例运行结果：

```golang
第一行 - c 的值为 31
第二行 - c 的值为 11
第三行 - c 的值为 210
第四行 - c 的值为 2
第五行 - c 的值为 1
第六行 - c 的值为 22
第七行 - c 的值为 21
```

---

## 关系运算符

  
下表列出了所有Go语言的关系运算符。假定 A 值为 10，B 值为 20。

| 运算符 | 描述 | 实例 |
| :--- | :--- | :--- |
| == | 检查两个值是否相等，如果相等返回 True 否则返回 False。 | \(A == B\) 为 False |
| != | 检查两个值是否不相等，如果不相等返回 True 否则返回 False。 | \(A != B\) 为 True |
| &gt; | 检查左边值是否大于右边值，如果是返回 True 否则返回 False。 | \(A &gt; B\) 为 False |
| &lt; | 检查左边值是否小于右边值，如果是返回 True 否则返回 False。 | \(A &lt; B\) 为 True |
| &gt;= | 检查左边值是否大于等于右边值，如果是返回 True 否则返回 False。 | \(A &gt;= B\) 为 False |
| &lt;= | 检查左边值是否小于等于右边值，如果是返回 True 否则返回 False。 | \(A &lt;= B\) 为 True |

以下实例演示了关系运算符的用法：

```golang
package main

import "fmt"

func main() {
   var a int = 21
   var b int = 10

   if( a == b ) {
      fmt.Printf("第一行 - a 等于 b\n" )
   } else {
      fmt.Printf("第一行 - a 不等于 b\n" )
   }
   if ( a < b ) {
      fmt.Printf("第二行 - a 小于 b\n" )
   } else {
      fmt.Printf("第二行 - a 不小于 b\n" )
   } 
   
   if ( a > b ) {
      fmt.Printf("第三行 - a 大于 b\n" )
   } else {
      fmt.Printf("第三行 - a 不大于 b\n" )
   }
   /* Lets change value of a and b */
   a = 5
   b = 20
   if ( a <= b ) {
      fmt.Printf("第四行 - a 小于等于 b\n" )
   }
   if ( b >= a ) {
      fmt.Printf("第五行 - b 大于等于 a\n" )
   }
}
```

以上实例运行结果：

```golang
第一行 - a 不等于 b
第二行 - a 不小于 b
第三行 - a 大于 b
第四行 - a 小于等于 b
第五行 - b 大于等于 a
```

---

## 逻辑运算符

下表列出了所有Go语言的逻辑运算符。假定 A 值为 True，B 值为 False。

| 运算符 | 描述 | 实例 |
| :--- | :--- | :--- |
| && | 逻辑 AND 运算符。 如果两边的操作数都是 True，则条件 True，否则为 False。 | \(A && B\) 为 False |
| \|\| | 逻辑 OR 运算符。 如果两边的操作数有一个 True，则条件 True，否则为 False。 | \(A \|\| B\) 为 True |
| ! | 逻辑 NOT 运算符。 如果条件为 True，则逻辑 NOT 条件 False，否则为 True。 | !\(A && B\) 为 True |

以下实例演示了逻辑运算符的用法：

```golang
package main

import "fmt"

func main() {
   var a bool = true
   var b bool = false
   if ( a && b ) {
      fmt.Printf("第一行 - 条件为 true\n" )
   }
   if ( a || b ) {
      fmt.Printf("第二行 - 条件为 true\n" )
   }
   /* 修改 a 和 b 的值 */
   a = false
   b = true
   if ( a && b ) {
      fmt.Printf("第三行 - 条件为 true\n" )
   } else {
      fmt.Printf("第三行 - 条件为 false\n" )
   }
   if ( !(a && b) ) {
      fmt.Printf("第四行 - 条件为 true\n" )
   }
}
```

以上实例运行结果：

```golang
第二行 - 条件为 true
第三行 - 条件为 false
第四行 - 条件为 true
```

---

## 位运算符

位运算符对整数在内存中的二进制位进行操作。

下表列出了位运算符 &, \|, 和 ^ 的计算：



```golang
A = 0011 1100

B = 0000 1101

-----------------

A&B = 0000 1100

A|B = 0011 1101

A^B = 0011 0001

~A  = 1100 0011
```



Go 语言支持的位运算符如下表所示。假定 A 为60，B 为13：

| 运算符 | 描述 | 实例 |
| :--- | :--- | :--- |
| & | 按位与运算符"&"是双目运算符。 其功能是参与运算的两数各对应的二进位相与。 | \(A & B\) 结果为 12, 二进制为 0000 1100 |
| \| | 按位或运算符"\|"是双目运算符。 其功能是参与运算的两数各对应的二进位相或 | \(A \| B\) 结果为 61, 二进制为 0011 1101 |
| ^ | 按位异或运算符"^"是双目运算符。 其功能是参与运算的两数各对应的二进位相异或，当两对应的二进位相异时，结果为1。 | \(A ^ B\) 结果为 49, 二进制为 0011 0001 |
| &lt;&lt; | 左移运算符"&lt;&lt;"是双目运算符。左移n位就是乘以2的n次方。 其功能把"&lt;&lt;"左边的运算数的各二进位全部左移若干位，由"&lt;&lt;"右边的数指定移动的位数，高位丢弃，低位补0。 | A &lt;&lt; 2 结果为 240 ，二进制为 1111 0000 |
| &gt;&gt; | 右移运算符"&gt;&gt;"是双目运算符。右移n位就是除以2的n次方。 其功能是把"&gt;&gt;"左边的运算数的各二进位全部右移若干位，"&gt;&gt;"右边的数指定移动的位数。 | A &gt;&gt; 2 结果为 15 ，二进制为 0000 1111 |

以下实例演示了逻辑运算符的用法：



```golang
package main

import "fmt"

func main() {

   var a uint = 60    /* 60 = 0011 1100 */  
   var b uint = 13    /* 13 = 0000 1101 */
   var c uint = 0          

   c = a & b       /* 12 = 0000 1100 */ 
   fmt.Printf("第一行 - c 的值为 %d\n", c )

   c = a | b       /* 61 = 0011 1101 */
   fmt.Printf("第二行 - c 的值为 %d\n", c )

   c = a ^ b       /* 49 = 0011 0001 */
   fmt.Printf("第三行 - c 的值为 %d\n", c )

   c = a << 2     /* 240 = 1111 0000 */
   fmt.Printf("第四行 - c 的值为 %d\n", c )

   c = a >> 2     /* 15 = 0000 1111 */
   fmt.Printf("第五行 - c 的值为 %d\n", c )
}
```

以上实例运行结果：

```golang
第一行 - c 的值为 12
第二行 - c 的值为 61
第三行 - c 的值为 49
第四行 - c 的值为 240
第五行 - c 的值为 15
```

---

