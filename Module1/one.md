#第一阶段

## 章节一

### 1.第一个go语言应用程序

```
package main

import "fmt"

func main() {
	fmt.Println("Hello World,go 语言之旅")
}
```

### 2.程序解析

```
package main	\\定义了包名，必须在源文件中非注释的第一行指明这个文件属于哪个包，如：package main;package main表示一个可独立执行的程序，每个go应用程序都包含一个名为main的包
import "fmt"	\\告诉go编译器这个程序需要fmt包（函数或者其他元素），fmt包实现了格式化Io的函数

func main() {	\\是程序的开始执行函数，main函数每个可执行的程序必须包含的，第一个执行的函数
	fmt.Println("Hello World,go 语言之旅") \\fmt.Println 可以将字符串输入到控制台上面，Println后面的ln是换行 \n
}
```

### 3.go语言开发基础知识介绍

#### 3.1 

* Go标记
  * Go程序可以由多个标记组成，可以是关键字，标识符，常量，字符串，符号

* 行分隔符
  * 在Go程序中，一行代表一个语句的结束。每个语句不需要像 C 家族中其它语言一样以 ; 结尾，因为这些工作都将由Go编译器自动完成

  * 如果你打算将多个语句写在同一行，他们必须使用 ;  人为区分，但在实际开发中我们不鼓励这种做法。    
​

#### 3.2 基础知识
*  文件名&关键字&标识符
	* 所有go源码以.go结尾；
   * 标识符以字母或者下划线开头，大小写敏感；
   * _ 是特殊标识符，用来忽略结果；
   * 保留关键字

###  4.Go程序的一般结构

```
1.Go程序是通过package来组织的，只有package名称为main的包可以包含main函数，一个可执行的程序，有且只有一个main包；
2.任何一个代码文件隶属于一个包；
3.通过import关键字来倒入其他非main包，比如 import("fmt")
									  import("os")
							  通常写成：import(
							  		   "fmt"
							  		   "os"
							  			) 
4. 通过func关键子声明函数：
	*a.同一个包中函数，直接调用；
	*b.不同包中函数，通过包名+点+函数名调用；
5.通过const关键字来进行常量的定义；
6.通过在函数体外使用var关键字来进行全局变量的声明和赋值；
7.通过type　关键字来进行结构体和接口声明；
8.包访问权限规则：
	*.函数名首字符大写即为Public，例如Println
	*.函数名首字符小写即为pvivate，包外包不能访问

```

### 5.实战一方法大写和小写的区别及放在不同包下面访问

#### 实战1

- 1.  写一个程序，对于给定一个数字n，求出所有两两相加等于n的组合;比如： 对于n=5，所有组合如下所示:
     1. 0 + 5 = 5
     2. 1 + 4 = 5
     3. 2 + 3 = 5
     4. 4 + 1 = 5
     5. 5 + 0 = 5
  2. 一个程序包含两个包add和main，其中add包中有两个变量：Name和age。请问main包中如何访问Name和age？

### 6.Go类型

* 布尔型:bool
  *  长度：1字节
  * 取值范围：true，false
  * 注意事项：不可用数字代表true或false
* 整型:int/uint
  * 根据运行平台可能为32或者64位

### 7.Go 语言的单个变量的声明与赋值

* 变量的声明格式：var <变量名称><变量类型>

* 变量赋值格式：<变量名称>=<表达式>

* 声明的同时赋值：var <变量名称> [变量类型] = <表达式>

* 简写 变量名 := 表达式

  ```
  package main

  import (
  	"fmt"
  )
  var aa = 22
  var ss = "kkk"
  var bb = true
  func variableZeroValue() {
  	//变量的声明格式：var <变量名称><变量类型>
  	var a int
  	var b  string
  	var c bool

  	//变量赋值格式：<变量名称>=<表达式>
  	a = 10
  	c = true
  	fmt.Printf("%d %q %v",a,b,c)
  	fmt.Println()
  }
 

  func variableInitValue() {
  	//声明的同时赋值：var <变量名称> [变量类型] = <表达式>
  	var a,b int = 2,3
  	var s string = "db"
  	fmt.Println(a,b,s)
  }

  func variableInitTypeValue() {
  	var a,b,s,c  =  2,3,"db",true
  	fmt.Println(a,b,s,c)

  }

  func variableShorter(){
  	//简写 变量名 := 表达式
  	a,b,s,c := 2,3,"db",true
  	s = "ddddddd"
  	fmt.Println(a,b,s,c)
  }

  func main() {
  	variableZeroValue()
  	variableInitValue()
  	variableInitTypeValue()
  	variableShorter()

  }

### 8.Go 语言的多个变量的声明与赋值
* 全局变量的声明可以使用var()方式进行简写；
* 全局变量的声明不可以省略var，但可以使用并行方式
* 所有变量都可以使用类型推断
* 局部变量不可以使用var的方式简写，只能使用并行方式
* 

```
 package main

	//全局变量的声明可以使用var()方式进行简写；
var (
	aa = 22
	bb = "kkk"
	cc = true

	//使用并列方式以及类型推断
	ddd,bbb=1,2
	
	//ccc :=2 //全局变量不支持这种形式
)

 //多个变量单独声明
	var a,b,c,d int
	//赋值
	a,b,c,d=1,2,3,4
   func main() {
}
```

### 9.Go 语言常量的赋值和使用以及iota的介绍

* 常量是一个简单值的标识符，在程序运行时，不会被修改的量

* 常量中的数据类型只可以是布尔型，数字型（整数型、浮点型和复数）和字符串型

* 常量的定义格式：

  * const identifier [type] = "abc"
  * 可以省略类型说明符[type],因为编译器可以根据变量的值来推断其类型
  * 显式类型定义： const b string = "abc"
  * 隐式类型定义： const b = "abc"

* 多个相同的类型：
  const a,b = 1,2

* 枚举

 ```
  package main

  import "fmt"

  func main() {
  	const LENGHT int = 10
  	const WIDTH = 5

  	var area  int

  	area = LENGHT * WIDTH

  	fmt.Printf("面积为：%d",area)
  	fmt.Println()

  	const a,b,c  =  1,false,"str"
  	fmt.Println(a,b,c)

  	/*const(
  		Unknow = 0
  		Female = 1
  		Male = 2
  	)
  	fmt.Println(unjknow)*/

  	const(
  		Unknow = iota
  		Female = iota
  		Male = iota
  	)
  	fmt.Println(Unknow,Female,Male)
  }
  ```

  

### 10.Go语言中包介绍

* https://go-zh.org/

### 11. for循环
* for的条件里面不需要括号；
* for的条件里可以省略初始条件，结束条件，递增条件
* 写一个程序，在终端打印出如下图形；   
			A    
			AA    
	                AAA    
	                AAAA    
	                AAAAA

```
package main

import "fmt"

func Print(n int) {
	for i :=0; i<=n+1; i++{
		for  j:=1; j<=i+1; j++{
			fmt.Printf("A")
		}
		fmt.Println()
	}
}

func main() {
	Print(10)
}
```

### 12 语言函数入门
#### 1. 介绍
* 1.声明语法： func  函数名(参数列表) [(返回值列表)]{}.    
	* func add() {}.   
	* func add(a int, b int) {}.  
	* func add(a int,b int) int {}.   
	* func add (a int,b int) (int, int) {}.  
	* func add (a, b int) (int, int) {}. 
* 2.函数特点
	* 不支持重载，一个包不能有两个名字一样的函数
	* 函数是一等公民，函数也是一种类型，一个函数可以赋值给变量，函数可以作为参数
	* 匿名函数
	* 多返回值   

#### 2. 案例
##### 2.1 example1
```
package main

import "fmt"

func add(a, b int) int{
	return a+b
}

func main() {
	d := add(4, 5)
	fmt.Println(d)
}
``` 

##### 2.2 example2
```
package main

import "fmt"

func add(a, b int) int{
	return a+b
}

func main() {
	//d := add(4, 5)
	c := add
	//fmt.Println(c)

	sum := c(4, 5)
	fmt.Println(sum)
}
```
### 13.高级语法函数作为参数
##### example1

```
package main

import (
	"fmt"
)

type add_func func(int,int)int

func add(a, b int) int {
	return a+b
}

func operator(op add_func, a int, b int) int {
	return  op(a,b)
}

func main() {
	c := add
	sum := operator(c,5,6)
	fmt.Println(sum)
}
```
##### example2
```
import "fmt"

type add_func func(int,int)int

/*func add(a, b int) int {
	return a+b
}*/

func sub(a, b int) int{
	return a-b
}


func operator(op add_func, a int, b int) int {
	return  op(a,b)
}

func main() {
	//c := add
	c := sub
	sum := operator(c,5,6)
	fmt.Println(sum)
}
```
##### example3 匿名函数
```
package main

import "fmt"

type add_func func(int,int)int


func operator(op add_func, a int, b int) int {
	return  op(a,b)
}

func main() {
	sum := operator(func(a int, b int) int {
		return a * b
	}, 5, 6)
	fmt.Println(sum)
}
```
### 14. 多返回值实践
#### example1
```
package main

	import "fmt"

	type add_func func(int,int)int

	func div(a, b int) (int, int) {
	return a/b, a%b
	}

	func operator(op add_func, a int, b int) int {
		return  op(a,b)
	}

	func main() {
		q,p :=div(9,4)
		fmt.Println(q)
		fmt.Println(p)
}

```

### 15. 可变参数
* func add(arg... int) int { 0个或多个参数};
* func add(a int,arg... int) int{1个或多个参数}；
* func add(a int, b int, arg... int )int{两个或多个参数}；
* 注意：其中arg是一个slice（切片），我们可以通过arg[index]依次访问所有参数通过len(arg)来判断传递参数的个数

#### 1.example
```
// 写一个函数add支持1个或者多个int相加，并返回相加值
package main

import "fmt"

func add(a int,arg... int) int {
	var sum int = a
	for i := 0; i < len(arg);i++ {
		sum += arg[i]
	}
	return  sum
}

func main(){
	sum := add(10, 2,3,4,5)
	fmt.Println(sum)

}
```

#### 2.example2
```
// 写一个函数concat，支持1个或者多个string相拼接，并返回结果
package main

import "fmt"

func concat(a string, arg... string)(result string) {
	result = a
	for i := 0; i < len(arg); i++ {
	result += arg[i]
	}
	return
}

func main() {
	res := concat("hello", " ", "world")
	fmt.Println(res)

}
```
