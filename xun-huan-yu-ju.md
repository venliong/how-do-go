# 语言 for 循环

for循环是一个循环控制结构，可以执行指定次数的循环。

### 语法

Go语言的For循环有3中形式，只有其中的一种使用分号。

和 C 语言的 for 一样：

```golang
for init; condition; post { }和 C 的 while 一样：
```

```golang
for condition { }
```

和 C 的 for\(;;\) 一样：

```golang
for { }
```

* init： 一般为赋值表达式，给控制变量赋初值；
* condition： 关系表达式或逻辑表达式，循环控制条件；
* post： 一般为赋值表达式，给控制变量增量或减量。

  


