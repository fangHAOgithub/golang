# 一：GO（golang）语言基础

### 1 golang介绍
```python
Go 即Golang，是Google公司2009年11月正式对外公开的一门编程语言
#2  解释型，编译型
Go是静态（编译型）强类型语言，是区别于解析型语言的弱类型语言(静态：类型固定 强类型：不同类型不允许直接运算)。
python动态强类型语言
#3 哪些是编译，哪些是解释
编译：java，c，c++，c#，go
解析型：python，js，php...
编译型语言涉及到跨平台，因为它需要编译成该平台的可执行文件，java--》运行在jvm之上
go：跨平台编译，交叉编译，在windows平台编译出mac上可执行
解释型：不存在跨平台问题，有解释器

#4 特性
跨平台的编译型语言，**交叉编译**
管道（channel），切片（slice），并发（routine）
有垃圾回收的机制
支持面向对象和面向过程的编程模式（go的面向对象没有类的概念）

# 5 发展（go是用c写起来的）
2009年11月7日 weekly.2009-11-06 —— 早期的版本
2015年8月19日 go1.5 —— 实现的架构变化，同时保留了和旧版本的兼容性,本次更新中移除了”最后残余的C代码”。# 从此以后，自举，自己写自己
2018年8月24日 go 1.11  ：modules，包管理

2020 年 8 月 go 1.15

# Go语言应用
中国的互联网公司，多多少少都会用，有些没用的，都在准备用
##### docker  k8s   蓝鲸 云计算  百度  小米:falcon
##### 七牛云 
## 应用领域，go适合做什么
服务的开发，微服务开发，运维相关，区块链，云平台
第一款开源区块链产品是用go写的


# Go语言发展前景，为什么火
很新，生态不完善
完美契合当下高并发的互联网生态
语法简单，速度快
云计算和区块链的火，互联网企业高并发的需求
```
---
### 2 开发环境搭建

```python
#1  ide,集成开发环境（goland等同于pycharm）
	-goland（jetbrains全家桶），vscode
    -推荐用goland，pycharm，idea，androidstudio
    一路下一步
#2 开发环境 sdk
一路下一步
# 测试安装成功
go version  把版本打印出来就装成功了

# 3注意事项（重点）
	-goland创建项目，选择go的安装路径（默认选中了）
    -gopath：所有的go代码必须放在这个路径下的src文件夹下，否则无法执行，默认创建到用户家目录下的go文件夹（mac,windows,linux）
   	-创建项目路径，go文件都不要出现中文
 
# 3 go命令

# 必须记住的
go env  # go的环境变量
	-GO111MODULE=空的，现在没有使用MODULE模式
    -GOPATH=C:\Users\fanghao\go #代码存放路径
    -GOROOT=D:\go # go sdk安装路径
go build  # 编译型语言，需要先编译再执行，编译成可执行文件，执行可执行文件
go run  # 编译并执行，开发阶段用，两步并作一步

# 其他不太需要记得
go get # 下载并安装包和依赖等同于pip install
go version
go fmt #运行gofmt进行格式化（go fmt ：自动将代码格式）

```
---
### 3 hello world
```go
//go语言的注释
//单行注释
/*
多行注释
多行注释
 */

// 重点
// go（所有编译型语言）项目要运行，必须有一个入口
// go的入口是main包下的main函数

// main包下可不可以有多个main函数：不可以

package main   //声明包名，包名是main，每一个go文件都属于某个包
import "fmt"    //导入包，内置包
func main() {   //定义了一个main函数，大括号包裹是函数体的内容
	fmt.Println("hello world") //打印函数等同与print()
}

// 编译 go build
//go build s1.go
// 执行
//s1.exe

// 编译并执行  go run
//go run s1.go
// 在goland中，右键，运行即可
```
---
### 4 变量

```go
package main
func main() {
	/*
	小结：
	    %T阔以查看类型
	    1、变量定义阶段就确定了，不允许改变
	    2、不可重复定义
	    3、先定义再使用，定义不使用会报错
	*/
    // 1 全定义
	//var 变量名 变量类型 = 变量值
    //var name string = "fanghao"
	// 2 类型推导   var 变量名 = 变量值
	//var name = "fanghao"
	// 3 简略声明变量   变量名 := 变量值
	//name := "fanghao"
	
	// 4 其他
	// 4.1只定义，不赋值
    //var age int   //必需声明类型，否则报错
    // 4.2 声明多个变量
	//var age, name string = "18", "fanghao"
	//var age, name = 18, "fanghao"
	//var name1, name2 = "张三", "fanghao"
	//name1, name2 := "张三", "fanghao"
	// 4.3 声明多个变量，赋初始值
	//var (
	//	name = "fanghao"
	//	age int = 18
	//	sex = 1
	//	height int
	//)
	//fmt.Println(name,age,sex,height)
	
	//4.4 小坑
	//var a = 1
	//a,b := 5,10  // 不报错，不是重复定义，只要赋值：左边，只有一个没有定义过的变量，就可以
	//fmt.Println(a,b)
}

```
---
### 5 变量规范
```go
//命名用驼峰，大小写有特殊意义
// 大小写敏感，Name和name不一样
//go 文件用下划线
//字母下划线开头，后面阔以数字/字母/下划线
//关键字和保留字不建议 用来做 变量名

/*
GO语言关键字
break      default       func     interface   select
case       defer         go       map         struct
chan       else          goto     package     switch
const      fallthrough   if       range       type
continue   for           import   return      var

go语言中有37个保留字，主要对应内建的常量、类型和函数
内建常量: true false iota nil
内建类型:  int int8 int16 int32 int64
          uint uint8 uint16 uint32 uint64 uintptr
          float32 float64 complex128 complex64
          bool byte rune string error
内建函数: make len cap new append copy close delete
          complex real imag
          panic recover
*/
```
---
### 6 类型
GO的数据类型很严格，不同的数据类型不能进行运算，需强制类型转换
```go
/*
    基础数据类型
    数据类型的默认值：
        数字类型是0
        字符串类型是 空字符串
        布尔类型   false
    整形
        int：根据不同的底层平台（Underlying Platform），
        表示 32 或 64 位整型。除非对整型的大小有特定的需求，否则你通常应该使用 int 表示整型。
        
        byte： 是int8     的别名
        rune： 是int832   的别名

        有符号整型
            int  在32位机器就是int32，64就是int64
            int8    高位一个符号位，2^7 - 1 ，-128-127
            int16
            int32
            int64
        无符号整型
            uint8   2^8 - 1 
            uint16
            uint32
            uint64
        浮点型 float64 是浮点数的默认类型
            float32     32 位浮点数
            float64     64 位浮点数
        复数
            complex64   实部和虚部都是 float32 类型的的复数
            complex128  实部和虚部都是 float64 类型的的复数
    字符串
        双引号包裹
        反引号包裹  `
    布尔
        bool true 和 false

*/
```
---
### 7 常量
* 常量是一个简单值的标识符，在程序运行时，不会被修改的量。
* 常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型。

```go
常量的定义格式：
const identifier [type] = value

-显式类型定义： const b string = "abc"
            const  变量名  变量类型 = 常量值
-隐式类型定义： const b = "abc"  // 类型推导
            const  变量名 = 常量值     // 类型推导
-多个相同类型的声明可以简写为：
    const c_name1, c_name2 = value1, value2
-其他方式：
    常量可以用len(), cap(), unsafe.Sizeof()函数计算表达式的值。
    常量表达式中，函数必须是内置函数，否则编译不过：
    const (
            name string = "fanghao"
            l = len(name)
            Female = 1
            Male = 2
        )
iota，特殊常量，可以认为是一个可以被编译器修改的常量。
iota 在 const关键字出现时将被重置为 0(const 内部的第一行之前)，
const 中每新增一行常量声明将使 iota 计数一次(iota 可理解为 const 语句块中的行索引)。
如下： 
    结果依次：
        0 1 2 ha ha 100 100 7 8
    const (
            a = iota   //0
            b          //1
            c          //2
            d = "ha"   //独立值，iota += 1
            e          //"ha"   iota += 1
            f = 100    //iota +=1
            g          //100  iota +=1
            h = iota   //7,恢复计数
            i          //8
        )
```


```go
package main

import "fmt"

func main() {
	const name string = "FANGHAO"
	fmt.Println(name)
}

```
---
### 8 函数基础
* 函数是基本的代码块，用于执行一个任务。
* Go语言最少有个 main() 函数。
* 你可以通过函数来划分不同功能，逻辑上每个函数执行的是指定的任务。
* 函数声明告诉了编译器函数的名称，返回类型，和参数。
* Go 语言标准库提供了多种可动用的内置的函数。例如，len() 函数可以接受不同类型参数并返回该类型的长度。如果我们传入的是字符串则返回字符串的长度，如果传入的是数组，则返回数组中包含的元素个数。

>函数中的参数列表和返回值并非是必须的，所以下面这个函数的声明也是有效的
```go
    func functionname() {  
    // 译注: 表示这个函数不需要输入参数，且没有返回值
    }
```
##### 空白符
>   _ 在 Go 中被用作空白符，可以用作表示任何类型的任何值。

##### 闭包函数
> 1 定义在函数内部  2对外部作用域有引用
```go
//定义方式
/*
	func 名字(参数名 类型，参数名 类型)(返回值类型，返回值类型){
		函数体内容
		return 返回值1，返回值2
	}
*/

// 1 有参数无返回值(定义函数)
//func add(a int,b int)  {
//	fmt.Println(a+b)
//}
// 1 调用函数
//add(2,3)


// 2 有参数无返回值,有多个相同类型参数
//func add(a ,b int)  {
//	fmt.Println(a+b)
//}
// 3 有参数无返回值,有多个相同类型参数，也有不同类型
//func add(a ,b int,msg string)  {
//	fmt.Println(a+b)
//	fmt.Print(msg)
//}
//  2调用 add(5,6)
//  3调用 add(5,6,"GGGG")

// 4 多个参数，一个返回值
//func add(a, b int) int {
//	return a + b
//}
// 4调用： 用变量接受返回值
//var a int =add(2,3)
//a := add(2, 3)
//fmt.Println(a)
// 4、1 多个参数，多个返回值，调用时需要多个变量接收返回值 a,b := add(1,2)
//func add(a, b int) (int,int) {
//	return a + b,a*b
//}
// 4.2多返回值，忽略一个返回值
//a,_:=add(3,4)
//fmt.Println(a)
//fmt.Println(_)  //

// 5、匿名函数(定义在函数内部的函数，不能是有名函数)，头等函数
//var a func()
//a = func (){
//	fmt.Println("我是匿名函数")
//}
//a()   // 直接调用匿名函数


// 6 命名返回值,如下
//func add(a, b int) (c int,d int) {
//	c=a+b
//	d=a*b
//	//return时，不需要再写c,d了
//	return
//}

// 7、函数是一等公民，可以赋值给变量
//  函数返回值为函数
//func test() func() {
//	return func() {
//		fmt.Println("我是返回函数")
//	}
//}
//  7、调用：函数返回值是函数
//a:=test()
//fmt.Println(a)  // 函数内存地址
//a()

// 8、函数返回值为函数,返回的函数带参数
// 类型只要有不一样的地方，就不是一个类型
//func test() func(msg string) {
//	return func(msg string) {
//		fmt.Println(msg)
//	}
//}
// 8、调用：函数返回值是函数
//a:=test()
//a("fanghao")  // 传入参数

//9 函数返回值为函数,返回的函数带参数,带返回值
//func test() func(a,b int) int{
//	return func(a,b int) int {
//		return a+b
//	}
//}
// 9、调用：函数返回值是函数
//var a func(a,b int)int   // 变量a  类型为  func(a,b int)int ，即函数test()的返回值
//a=test()                  //赋值
//fmt.Println(a(2,3))       //调用

//10 函数参数为函数类型，返回值为带参数，带返回值的函数类型
//func test(f func()) func(a,b int) (int,int){
//	return func(a,b int) (int,int) {
//		f()
//		return a+b,a*b
//	}
//}
// 10、调用：函数返回值是函数
// 方式1，写在一起
//a,b:=test(func() {
//	fmt.Println("我是函数参数")
//})(3,4)
// 方式2
//f:= func() {
//	fmt.Println("我是函数参数")
//}
//
//f1:=test(f)
//a,b:=f1(3,4)
//fmt.Println(a,b)


//11 闭包函数
//func test(age int) func()  {
//	a:= func() {
//		fmt.Println(age)
//	}
//	return a
//}

//12 类型重命名
//var a MyFunc =test()
//c,d:=a(1,2)
//fmt.Println(c,d)
// 
//func test()MyFunc  {
//      return func(a,b int)(int,string) {
//      fmt.Println("xxx")
//      return 10,"ok"
//      }
//  }

```

---
### 9 变量作用域
* 作用域为已声明标识符所表示的常量、类型、变量、函数或包在源代码中的作用范围。
* Go 语言中变量可以在三个地方声明：
* 函数内定义的变量称为局部变量
* 函数外定义的变量称为全局变量
* 函数定义中的变量称为形式参数

//在同一个包下，函数名不能重名
//全局变量，全局有效，只要改了，就是改了

```go
var a int   //全局变量，全局有效，只要改了，就是改了
func main() {
	var a int
	fmt.Println(a)  //0
	a=19
	fmt.Println(a) //19
	test1()  // 0
	fmt.Println(a) //19
}

func test1()  {
	fmt.Println(a)

}
```

#### 1-9 小结一
##### 一
- 任何一个go语言的程序，必须有入口（main包下的main函数），所有的编译型语言都会有入口
- go文件第一行 ，声明包 package 包名
- 导入需要使用的包（goland，不用手动导入，自动导入），包导入了不使用会报错
- 在goland中，敲main 回车，自动补齐
- 在大括号里写函数体的内容（跟代码缩进没有任何关系）
- 让程序运行起来
- 先编译(相应平台的可执行文件)，再执行
- 编译并执行  go run
- goland中，右键run即可，编译并运行
##### 二、变量
- 全定义        var name string ="fanghao"
- 类型推导      var name ="fanghao"
- 简略声明       name :="fanghao"

- 不写类型不代表没有类型，变量在定义阶段，类型就固定了，而且不能改变
- 变量定义了必须使用，否则报错
- 变量要先定义再使用，并且不能重复定义
- 强类型，不同类型之前不能直接运算（强制类型转换）

##### 三、函数
- func 函数名(参数1 类型，参数2 类型)(返回值类型，返回值类型){}
- 空白符（忽略掉某个返回值 _  ）
- 匿名函数（定义在函数内部，没有名字）
- 类型只要有一点点不一样就不是同一个类型，不是同一个类型就不能相互赋值，相互运算
- 闭包：1 定义在函数内部 2 对外部作用域有引用
- 给类型重命名（他们是两种类型） 函数类型，可以简写
- 没有关键字传参
- 没有默认参数
---

# 二、包、条件、循环、switch、数组、切片

### 1、包
```python
#1  包：模块的意思
#2 自定义包
	-go语言的代码必须放在gopath的src路径下
    -包导入是从gopath的src路径下开始检索（开始找）
    -除了main包以外，建议包名就叫文件夹名，一个文件夹下的包名必须一致
    -同一个包下，变量，函数只能定义一次
    -同一个包下的变量和函数可以直接使用
    -包内的函数或变量，想让外部包使用，必须首字母大写
    -以后下的第三方包都是放在gopath的src路径下
# 3 init函数（特殊函数）
	-不需要调用就会执行
    -可以定义多个
# 4 包导入的几种方式
	-import "day02/mypackage"
    -给包重命名
    	-import 名字 "day02/mypackage"
        -使用：名字.变量/函数
    -包只导入，不使用
    import _ "day02/mypackage"
 
# 5 go语言没有一个统一包管理的地址，大家都放到github上

# 6 采用go mode模式
	-两种创建方式之一
    	-命令行下输入：go mod init 项目名   在当前路径下创建出go.mod(该项目依赖go的版本，第三方包版本)
        -项目路径的cmd窗口，go get 第三方包，就会在go.mod中加入依赖
        -以后把项目copy给别人，go install
        -自己写的包，就放在自己项目路径下
        -加代理的方式：手动写，goland中配置
   	-在goland中创建项目时，直接指定modules，可以配置环境变量（加代理）
```
---
### 2、条件语句： if-else
* 基础使用
```python
    # 方式1：
    if 条件 { 
        代码块
        }
    # 方式2：
    if 条件1 { 
        代码块1
    }else if 条件2{
        代码块2
    }else{
        代码块3
    }
```
*注意事项：条件后不能回车
---
### 3、循环
* for 是 Go 语言唯一的循环语句。Go 语言中并没有其他语言比如 C 语言中的 while 和 do while 循环。
* for 循环语法
for 初始变量 ; 条件 ; 变量自增/自减{
    循环体
}
```go
for initialisation; condition; post {  
    }
	
//1、
for i:=0;i<10;i++{
	fmt.Println(i)  // 变量i 作用域，只有循环体中才可以使用
}
//2、省略第一
i:=0   //作用域范围大，不止在for内部，外部也可以用
for ;i<10;i++{
	fmt.Println(i)
}
//3、省略第三部分
i:=0   //作用域范围大，不止在for内部，外部也可以用
for ;i<10;{
	fmt.Println(i)
	i++   //循环自增写在循环体中
}
//4、省略一和三部分的简略写法（这就是while循环）  for 条件{ 循环体内容}
i:=0
for i<10{
	fmt.Println(i)
	i++
}
//5 死循环
for {
	fmt.Println("ssssss")
}

//6 break continue
//break：  结束本次
//continue： 结束本次循环，继续下一次循环
```

---
### 4、switch语句  和 goto
* switch 是一个条件语句，用于将表达式的值与可能匹配的选项列表进行比较，并根据匹配情况执行相应的代码块。它可以被认为是替代多个 if else 子句的常用方式。
* Go 语言的 goto 语句可以无条件地转移到过程中指定的行。
* goto 语句通常与条件语句配合使用。可用来实现条件转移， 构成循环，跳出循环体等功能。
* 但是，在结构化程序设计中一般不主张使用 goto 语句， 以免造成程序流程的混乱，使理解和调试程序都产生困难。
```python
基本语法
    switch 表达式（可省略）{
        case 值/表达式/多表达式:
            代码块
        defalut:
            默认情况
    }
```

```python
    # 1、基本使用和默认情况
    num := 2
    switch num {
        case 1:
            ...
        case 2:
            ...
        default:
            默认情况
    }
    # 2、多表达式
    num := 40
    switch num {
        case 1,2,3,4,5:
            ...
        case 7:
            ...
        default:
            默认情况
    }
    # 3、无表达式
    num := 40
    switch {
        case num==1,num==2:
            ...
        case num==3:
            ...
        default:
            默认情况
    } 
    # 4、Fallthrough语句，穿透，只要代码块中有，就会无条件执行下一个case / default
    num := 40
    switch {
        case num==1,num==2:
            ...
        case num==3:
            fmt.Println("3")
            Fallthrough  // 穿透，只要代码块中有，就会无条件执行下一个case / default
        default:
            默认情况
    }
    
    
```

---
### 5 数组
* 数组是同一类型元素的集合。例如，整数集合 5,8,9,79,76 形成一个数组。
* Go 语言中不允许混合不同类型的元素，例如包含字符串和整数的数组。（当然，如果是 interface{} 类型数组，可以包含任意类型）
* 内存中连续存储
* 数组的大小在定义阶段就已经确定，不能更改
* 数组的大小是类型的一部分，即[2]int 和 [3]int 不是同一个类型
* 数组是值类型，函数传参是copy传参，如果是值类型，函数内改了，不会影响原来，看如下例子的第4条
* 数组长度，用内置函数，len()，长度在定义阶段就确定
* range迭代，如果用一个变量接收，就是索引，两个变量接收就是 索引+value
```go
    //1、定义数组
    //var names [3]string
    //var ages [3]int
	
    //2、赋值
    //var ages [3]int
    //ages[0] == 77
	
    //3、定义并初始化
    //var ages [3]int=[3]int{1,2,3} //[1,2,3]
    //var ages [3]int=[3]int{1,2}   //[1,2,0]
    //var ages [3]int=[3]int{}      //[0,0,0]
    //var ages=[3]int{}
    //ages:=[3]int{1,3,4,7}  //不允许多放
	//3.1、定义并初始化其他
	//var ages = [...]int{1,2,3,4,5}
	//ages := [...]{1,2,3}
	//注意，这种是错的 var ages [5]int= [...]int{1,2,3,4,5}  // 不支持
	
	//4 指定位置
    //var names [100]int=[100]int{10:99,99:99}
    //var names [100]int=[100]int{10,11,2,44,99:99,45:88}

    //5 值类型
    //var a [2]int=[2]int{1,2}
    //fmt.Println(a)    //[1,2]
    //test5(a)  //因为数组是值类型，go函数传参，都是copy传递，如果是值类型，函数内改了，不会影响原来的
    //fmt.Println(a)    //[1,2]
    //func test5(a [2]int)  {
    //    a[0]=99
    //    fmt.Println(a)
    //}
	
	//6、列表循环，两种方式
	// 方式1
    //var a =[...]int{7,4,3,5,6,7}
	// 方式1：普通循环
    //for i:=0;i<len(a);i++{
    //	fmt.Println(a[i])
    //}
	//方式2：通过range来循环  (range不是内置函数，是一个关键字，for，if，else),打印出索引
    //for i:=range a{
    //	fmt.Println(i)
    //}
	
	//7 多维数组
	//var a [2][3]int   //定义
	//a[0][0] = 88      //赋值
    //var a [2][2]int = [2][2]int{{1,2},{3,4}}  //定义&赋值
	
	
```
---
### 6 切片
* Go 语言切片是对数组的抽象。
* Go 数组的长度不可改变，在特定场景中这样的集合就不太适用，Go 中提供了一种灵活，功能强悍的内置类型切片("动态数组")，
*与数组相比切片的长度是不固定的，可以追加元素，在追加时可能使切片的容量增大。

* a[start:end] 创建一个从 a 数组索引 start 开始到 end - 1 结束的切片，属于**前闭后开**
* b=a[:],缺少开始和结束值。开始和结束的默认值分别为 0 和 len (numa)
* 切片的长度是切片中的元素数。切片的容量是从创建切片索引开始的底层数组中元素数。
* 内存优化:切片持有对底层数组的引用。只要切片在内存中，数组就不能被垃圾回收。
    一种解决方法是使用 copy 函数 func copy(dst，src[]T)int 来生成一个切片的副本。这样我们可以使用新的切片，原始数组可以被垃圾回收。
    copy(old, new)
######注意事项
* 切片类型的零值为 nil。一个 nil 切片的长度和容量为 0。可以使用 append 函数将值追加到 nil 切片。
* 修改切片，会影响原数组，反之亦然（修改原数组，也会影响切片）
* 切片自己不拥有任何数据。它只是底层数组的一种表示。对切片所做的任何修改都会反映在底层数组中。
* `func make（[]T，len，cap）`[]T 通过传递类型，长度和容量来创建切片。容量是可选参数, 默认值为切片长度。make 函数创建一个数组，并返回引用该数组的切片。
* 坑：slice或者array作为函数参数传递的时候，本质是传值而不是传引用。传值的过程复制一个新的切片，这个切片也指向原始变量的底层数组。（个人感觉称之为传切片可能比传值的表述更准确）。函数中无论是直接修改切片，还是append创建新的切片，都是基于共享切片底层数组的情况作为基础。也就是最外面的原始切片是否改变，取决于函数内的操作和切片本身容量。
* 引用类型，空值是nil，当作参数传递（append有可能会出问题）
```go
    //1、基于数组，做切片
    //var a [10]int = [10]int{0,1,2,3,4,5,6,7,8,9}
    //var b []int   //[]中不带东西，就属于切片类型
	//b = a[:]      //
	
	//2、使用make创建切片
    //a := make([]int, 5, 5)
	
	//3、使用切片，a[0],a[1]...，根据索引取值
	
	//4、切片的长度和容量、追加元素
	// 长度len()，容量cap()
	//var a =[10]int{9,8,7,6,5,4,3,2,1,0}
    //var b []int=a[7:8]    //[2]，左闭右开区间
	//len(b)  //1   元素个数
    //cap(b)  //3   最多还能放几个（即a[7:]，取到尾，能放3个）
	// append()，追加元素
    //b=append(b,3)
    //b=append(b,999)
    ////到了临界点再追加
    //b=append(b,888)
    //len(b)  //4   元素个数
    //cap(b)  //6   在上一次的基础上 * 2，即3*2=6
	
	//5多维切片
    //pls := [][]string {
    //        {"C", "C++"},
    //        {"JavaScript"},
    //        {"Go", "Rust"},
    //    }
```


# 三、可变参数函数，map，指针，结构体，方法，接口
---
### 1 可变参数函数

* 可变参数函数是一种参数个数可变的函数。
* 如果函数最后一个参数被记作 ...T ，这时函数可以接受任意个 T 类型参数作为最后一个参数。 只有函数的最后一个参数才允许是可变的。

* `func find(num int, nums ...int)` 中的 nums 可接受任意数量的参数。在 find 函数中，参数 nums 相当于一个整型切片。

* 给可变参数函数传入切片
定义时：      func find(num int, nums ...int)
调用：        find(89, nums...)    //nums 是切片

---
### 2 map
* map 是在 Go 中将值（value）与键（key）关联的内置类型。通过相应的键可以获取到值。
* 通过向 make 函数传入键和值的类型，可以创建 map，语法`var a map[string]string = map[string]string{key:value}`
* `make(map[type of key]type of value)`是创建 map 的语法。
* map 的零值是 nil。如果你想添加元素到 nil map 中，会触发运行时 panic。因此 map 必须使用 make 函数初始化。
* 遍历时，有一点很重要，当使用 for range 遍历 map 时，不保证每次执行程序获取的元素顺序相同。
* Map 是引用类型 和 slices 类似，当map被赋值为一个新变量的时候，它们指向同一个内部数据结构。因此，改变其中一个变量，就会影响到另一变量。
* map 之间不能使用 == 操作符判断，== 只能用来检查 map 是否为 nil，判断两个 map 是否相等的方法是遍历比较两个 map 中的每个元素
```go
    //1、通过make创建map
    //money := make(map[string] int)   //key是string，value是int的map
	
	//2、添加元素
    //money["fanghao"] = 99999
	
	//3、创建并初始化
    //语法var a map[string]string = map[string]string{key:value}
    //var a  map[string] int = map[string] int{"name" : 12, "age" : 20}
    //var a = map[string] int{"name" : 12, "age" : 20}
    //a  := map[string] int{"name" : 12, "age" : 20}
	
    //	4、修改/新增
	//a["name"] = 999     //有则修改，无则新增
	//a["age"] = 999      //修改
	//a["gggg"] = 999     //新增
    
	//5、获取元素，map中到底是不是存在这个 key，语法value, ok := map[key]
	//a["hhh"]           //取值，没有则返回空值
    //value, ok := a["h"] //无这个值，所以value=0，ok=false
	
	//6、遍历，通过range，key,value := range map，即可获取key和value
	
`	//7、删除map中的元素，通过delete(map,key),没有返回值

    //8、获取长度，通过len()

```

---
### 3 指针
* 一个指针变量可以指向任何一个值的内存地址，它所指向的值的内存地址在 32 和 64 位机器上分别占用 4 或 8 个字节，占用字节的大小与所指向的值的大小无关。
* 当一个指针被定义后没有分配到任何变量时，它的默认值为 nil。指针变量通常缩写为 ptr。
* 指针是一种存储变量内存地址（Memory Address）的变量。（指针是存储地址的变量）
* 指针声明：指针变量的类型为 `*T`，该指针指向一个 T 类型的变量。
* 放在类型前，表示指向该类型的指针（变量定义，指定类型时才会用到） 
* `&` 操作符用于获取变量的地址
* `*` 放在变量前，表示解引用（取出指针指向的具体的值）
* 指针的解引用可以获取指针所指向的变量的值。将 a 解引用的语法是 *a。(获取指针存储的内存地址中，存放的值)
* a[x] 等价于 (*a)[x],a[x] 是 (*a)[x] 的简写形式
* Go 不支持指针运算
* 创建指针的另一种方法——new() 函数
- `str := new(string)`
- `*str = "Go语言教程"`
##### 注意事项
* 数组指针 ：它是一个指针，但是数据类型为数组，或者说指向数组 `*[3]int`表示指向数组的指针，它是指针
* 指针数组 ：它是一个数组，该数组的元素都为地址值`[3]*int` 里面是三个指针的数组，它是数组，存的是三个指针变量
* `*`操作符作为右值时，意义是取指针的值，作为左值时，也就是放在赋值操作符的左边时，表示 a 指针指向的变量。
* 其实归纳起来，*操作符的根本意义就是操作指针指向的变量。 当操作在右值时，就是取指向变量的值，当操作在左值时，就是将值设置给指向的变量。

---
### 4、结构体
* 定义：使用关键字 type 可以将各种基本类型定义为自定义类型，基本类型包括整型、字符串、布尔等。结构体是一种复合的基本类型，通过 type 定义为自定义类型后，使结构体更便于使用。
* 字段首字母大小表示对外开放（public），小写表示隐藏属性
* 结构体的零值是属性的零值，它是值类型，参数传递是copy传递，在函数中修改，不会影响原来的
* 匿名结构体（定义在内部（函数，结构体），只使用一次，没有名字）
* 访问和修改结构体字段，通过 `.` 访问，大小写敏感
* 匿名字段（字段没有名字，只有类型），匿名字段类型就是字段名，所有类型不能重复
* 结构体相等性，结构体是值类型。如果它的每一个字段都是可比较的，则该结构体也是可比较的。如果两个结构体变量的对应字段相等，则这两个变量也是相等的。
* 如果结构体包含不可比较的字段，则结构体变量也不可比较。
```go
    // 1、定义
    //type 类型名 struct {
    //    字段1 字段1类型
    //    字段2 字段2类型
    //    …
    //}
	
	// 2、命名结构体
    //type  GGG struct {    //首字母大小表示对外开放
    //    Name string   //首字母大小表示对外开放
    //    Age int
    //    Sex string
    //}
	
	// 3、定义并赋初值
    ////var per entity.GGG=entity.GGG{Name:"fanghao"}     //指名道姓，不按位置，可以少传
    //var per2 entity.GGG=entity.GGG{"fanghao",19,"男"}      //按位置，必须全传
    //fmt.Println(per2)
    //per2.Age=20
    //fmt.Println(per2)
	
	// 4、匿名结构体（定义在内部（函数，结构体），只使用一次，没有名字）
    // 有什么用？当定义多个变量（想一次使用），就可以把这多个变量放到匿名结构体中
    //a := struct {
    //    HobbyId int
    //    HobbyName string
    //}{}
    //a.HobbyId = 1
    //a.HobbyName = "足球"
    //fmt.Println(a)  //{1 足球}

    // 5、访问和修改结构体字段，通过 `.` 访问，大小写敏感
	
	// 6、结构体的指针
    //var g *entity.GGG
    //fmt.Println(g)      // <nil>
	
	// 定义并初始化
    //var g *entity.GGG = &entity.GGG{}
    //fmt.Println(g)
	//给属性赋值，g是指向这个结构体的指针，获取值需要解引用，即 *g，
	//(*g).Name = "fanghao"     //
    //g.Name = "fanghao111"     //支持直接使用(数组也是这样，自动帮你处理了)
	
	// 7、匿名字段（字段没有名字，只有类型）
	//main外定义：
    //定义一个结构体，内涵匿名字段（字段没有名字）  匿名字段类型就是字段名，所有类型不能重复
    //type GGG struct {
    //	string
    //	int
    //	sex string
    //}
	//使用
    //var g = GGG{"FANGHAO",18,"MALE"}
    //fmt.Println(g)
    //fmt.Println(g.string)
    //fmt.Println(g.int)
    //g.int = 55        // 改值
    //fmt.Println(g)

    // 8、嵌套结构体(结构体中套结构体)
	//定义
    //type Person struct {
    //	Name string
    //	Age int
    //	Hobby Hobby
    //}
    //type Hobby struct {
    //	HobbyName string
    //}
	// 初始化，传值，按位置和按关键字，和此前一致
    //var per = Person{
    //    Name: "fanghao",
    //    Age: 20,
    //    Hobby: Hobby{
    //        HobbyName: "篮球",
    //        },
    //    }

    // 9、字段提升，如果是结构体中有匿名的结构体类型字段，则该匿名结构体里的字段就称为提升字段。
	//  这是因为提升字段就像是属于外部结构体一样，可以用外部结构体直接访问
	//  如果有字段一样的，优先用自己的
	// 定义
    //type Person struct {
    //        Name string    //  如果有字段一样的，优先用自己的 
    //        Age int
    //        Hobby       // 该字段是匿名结构体
    //    }
    //type Hobby struct {
    //        HobbyName string
	//        // Name string    //  如果有字段一样的
    //    }
    
    // 使用
	//fmt.Println(per.Name)
    //fmt.Println(per.HobbyName)
	
	// 10、导出结构体和字段 **大写字母开头**,在外部包可以使用
	
	
```

---
### 5、方法
* 方法其实就是一个函数，在 func 这个关键字和方法名中间加入了一个特殊的接收器类型。
* 接收器可以是结构体类型或者是非结构体类型。接收器是可以在方法的内部访问的。
```go
创建了一个接收器类型为 Type 的方法 methodName
func (t Type) methodName(parameter list) {
}
```
* 指针接收器与值接收器，想改原来的，就用指针，不想改原来的就用值（指针用的多）
* 不管是值还是指针来调用，只要是值类型接收器，改的就是新的，只要是指针类型接收器，改的是原来的
* **值接收器**，可以用值来调，也可以用指针来调，函数的值参数，只能**传值**
* **指针接收器**，可以用值来调，也可以用指针来调，函数的指针参数，只能**接收指针**

##### 注意事项
* 补充，当拷贝一个结构体的代价过于昂贵时。考虑下一个结构体有很多的字段。在方法内使用这个结构体做为值接收器需要拷贝整个结构体，这是很昂贵的。在这种情况下使用指针接收器，结构体不会被拷贝，只会传递一个指针到方法内部使用。
* 在其他的所有情况，值接收器都可以被使用。
* 给非结构体绑定方法，不允许给内置的类型绑定
```go
    //以下不允许
    //func (i int) add()  {
    //	i += 1
    //}
    //var b = 5
    //b.add()
```
* 自定义类型，运算只能和自定义类型的运算，即使`type Newint int`, Newint 类型也不阔以和 int 类型进行运算，需强制类型转换
```go
    //type Newint int
    ////var a Myint =10
    //var b =11
    //fmt.Println(a+b)  //类型不匹配
    //c:=a+Myint(b)
    //fmt.Println(a+Myint(b))  //类型匹配
    //d:=int(a)+b
    //fmt.Println(int(a)+b)  //类型匹配
```

```go
    // 1、简单定义和使用
	// 定义
    //type Person2 struct {
    //    Name string
    //    Age int
    //}
    //定义一个方法  : (p Person2) 绑定给了Person2结构体的对象，在方法中使用值接收器
	//func (p Person2) printName()  {
    //   //在方法内可以使用p
    //   fmt.Println(p.Name)
    //}
	// 假如使用函数方式，需要手动传值，在函数中使用值参数
    //func printName(p Person2)  {
    //	fmt.Println(p.Name)
    //}
    // 使用1，使用方法
    //per := Person2{}
    //per.Name = "fanghao"
    //per.printName()   // fanghao
    // 使用2，使用函数，需要手动传值
    // 假如使用函数方式，需要手动传值
    //func printName(p Person2)  {
    //	fmt.Println(p.Name)
    //}
    //per1 := Person2{Name: "FANGHAO"}
    //printName(per1)		//需要手动传值
	
	// 2、指针接收器与值接收器，改值
    //修改名字，值接收器
    //func (p Person2) changeName(name string)  {
    //  p.Name=name
    //  fmt.Println(p)
    //}
    //per1 := Person2{Name: "FANGHAO"}
    //per1.changeName("GGGG")
    //fmt.Println(per1)     //{FANGHAO 0}，没有改
    //修改名字，指针接收器
    //func (p *Person2) changeName(name string)  {
    //  p.Name=name     // (*p).Name=name ,解引用
    //  fmt.Println(p)
    //}
    //per1 := Person2{Name: "FANGHAO"}
    //per1.changeName("GGGG")
    //fmt.Println(per1)     //{GGGG 0}，使用指针会被改
	
	// 3、匿名字段的方法（方法提升）
    //type Person2 struct {
    //	Name string
    //	Age int
    //	Hobby  //匿名字段
    //}
    //type Hobby struct {
    //	Name string
    //}
    ////给结构体绑定方法
    //func (p Person2)printName()  {
    //	fmt.Println(p.Name)
    //}
    //func (h Hobby)printHobbyName()  {
    ////func (h Hobby)printName()  {    // 方法名重了的话，优先用自己的
    //	fmt.Println(h.Name)
    //}
	// 使用
    //per1 := Person2{Name: "fanghao",Age: 18,Hobby:Hobby{Name: "足球"}}
    //per1.printHobbyName()     //Hobby是匿名字段，但是可以直接访问到它的方法，方法提升
    //per1.printName()
	// 方法名重了的话，优先用自己的，要访问必须指名道姓
	//per1.Hobby.printHobbyName()
	
	// 4、在方法中使用值接收器 与 在函数中使用值参数
    //type Person2 struct {
    //	Name string
    //	Age int
    //}
    ////在方法中使用值接收器
    //func (p Person2)printName()  {
    //	fmt.Println(p.Name)
    //}
    //func (p Person2)changeName(name string)  {
    //	p.Name=name
    //	fmt.Println(p)
    //}
    ////在函数中使用值参数
    //func printName(p Person2)  {
    //	fmt.Println(p.Name)
    //}
    // 使用1，可以传值
    //per1:=Person2{Name: "fanghao"}
    //per1.printName()
    //printName(per1)
	// 使用2，可以传指针
    //per1:=&Person2{Name: "fanghao"}  //per1是个指针
    //per1.printName()
    //printName(*per1)
    // 测试改值
    //per1:=&Person2{Name: "fanghao"}  //per1是个指针
    //per1.changeName("fanghao55523")   // {fanghao55523 0}
    //fmt.Println(per1)                 // &{fanghao 0} 原来的值没有被改

    // 5、在方法中使用指针收器 与 在函数中使用指针参数
    //type Person2 struct {
    //	Name string
    //	Age int
    //}
    ////在方法中使用值接收器
    //func (p *Person2)printName()  {
    //	fmt.Println(p.Name)
    //}
    //func (p *Person2)changeName(name string)  {
    //	p.Name=name
    //	fmt.Println(p)
    //}
    ////在函数中使用指针参数
    //func printName(p *Person2)  {
    //	//fmt.Println((*p).Name)
    //	fmt.Println(p.Name)
    //}
    // 使用1，值可以来调用
    //per1:=Person2{Name: "fanghao"}
    //per1.printName()  //值可以来调用
    //printName(&per1)
    // 使用2，指针可以来调用
    //per1:=&Person2{Name: "fanghao"}
    //per1.printName()  //指针可以来调用
    //printName(per1)
    // 测试改值，值传入
    //per1:=Person2{Name: "fanghao"}
    //per1.changeName("fanghao55523")   // &{fanghao55523 0}
    //fmt.Println(per1)                 // {fanghao55523 0}
    // 测试改值，指针传入
    //per1:=&Person2{Name: "fanghao"}
    //per1.changeName("fanghao55523")   // &{fanghao55523 0}
    //fmt.Println(per1)                 // &{fanghao55523 0}

	// 6、非结构体上绑定方法
    //type Newint int   //自定义类型Newint
    //
    //func (n *Newint) AddOne() Newint {
    //	(*n) = (*n) + 1
    //	return (*n)
    //}
	// 使用
    //var a Newint = 10
    //fmt.Println(a)    // 10
    //a.AddOne()
    //a.AddOne()
    //a.AddOne()
    //a.AddOne()
    //fmt.Println(a)    // 14

```
---
### 6、接口
* 面向对象的领域里，接口一般这样定义：接口定义一个对象的行为，规范子类对象的行为
* 接口是一系列方法的集合（规范行为）
* 当一个类型定义了接口中的所有方法，我们称它实现了该接口。接口指定了一个类型应该具有的方法，并由该类型决定如何实现这些方法。

* 语法
```go
type 接口类型名 interface{
    方法名1( 参数列表1 ) 返回值列表1
    方法名2( 参数列表2 ) 返回值列表2
    …
} 
```
* 类型断言，语法：`value, ok = x.(T)`，x：表示类型为interface{}的变量，T：表示断言x可能是的类型。
* 该语法返回两个参数，第一个参数是x转化为T类型后的变量（也就是 value），第二个值是一个布尔值（也就是 ok），若为true则表示断言成功，为false则表示断言失败。

##### 注意事项/拓展
* 侵入式接口（接口没了，子类报错）和非侵入是接口（接口没了，不影响代码，go语言中的接口是非侵入式的）

```go
    //1 定义接口（定义一个鸭子接口，speak方法，run方法）
    //// 定义一个鸭子接口，Speak，Run方法
    //type Duck interface {
    //	Speak()
    //	Run()
    //}
    //
    //// 普通鸭子
    //type PDuck struct {
    //	name string
    //}
    //// 唐老鸭
    //type TDuck struct {
    //	name string
    //	age int
    //}
    //// 实现Duck接口
    //func (p PDuck) Speak()  {
    //	fmt.Println("普通鸭子嘎嘎叫")
    //}
    //func (p PDuck) Run()  {
    //	fmt.Println("普通鸭子走")
    //}
    //func (p TDuck) Speak()  {
    //	fmt.Println("唐老鸭说人话")
    //}
    //func (p TDuck) Run()  {
    //	fmt.Println("唐老鸭跑路")
    //}
	// 使用1
    //pd := PDuck{name: "p鸭子"}
    //pd.Speak()
    //pd.Run()
    //td := TDuck{name: "t唐老鸭"}
    //td.Speak()
    //td.Run()
    // 使用2，接口类型变量(可以理解为多态的体现)
    //var duck Duck
    //pduck:=PDuck{"黑子"}
    //tduck:=TDuck{"egon",1}
    //duck=pduck
    //duck.Run()
    //duck=tduck  //多态，同一类事务多种形态
    //duck.Run()
	
	// 3、类型断言
    //var duck Duck =TDuck{"fanghao",1}
    ////断言是TDuck类型
    //v, ok := duck.(TDuck)
    ////断言成功，ok是true，v就是TDuck结构体对象
    //fmt.Println(v)
    //fmt.Println(v.name)
    //fmt.Println(ok)
    //var v PDuck
    //var ok bool
    //v, ok = duck.(PDuck)
    ////断言失败,ok是false，v是PDuck类型的空置，因为没有赋值
    //fmt.Println(ok)
    //fmt.Println(v)
	
	// 4、类型选择，通过switch，相比于大量的if 判断，更加优雅，可读性更好
	// 方式1，定义，通过if 
    //func tes(duck Duck){
    //	if v,ok := duck.(TDuck);ok{
    //		fmt.Println(ok)
    //		fmt.Println("我是唐老鸭")
    //		fmt.Println(v)
    //	}else if v,ok := duck.(PDuck);ok {
    //		fmt.Println("我是普通鸭子")
    //		fmt.Println(v)
    //	}
    //}
    // 方式2，定义，通过switch，类型选择
    //func tes1(duck Duck) {
    //	switch v:=duck.(type) {
    //	case PDuck:
    //		fmt.Println(v)
    //		fmt.Println("我是普通鸭子")
    //	case TDuck:
    //		fmt.Println(v)
    //		fmt.Println("我是唐老鸭")
    //	}
    //}
	// 调用
    //var p PDuck = PDuck{name: "普通鸭"}
    //var p TDuck = TDuck{name: "t鸭"}
    //tes(p)
    //tes1(p)

    // 5、空接口（没有任何方法，所有的数据类型都实现了空接口）
	// 定义
    //type Empty interface {
    //}
	// 类型选择
    //func tes3(b Empty)  {
    //	switch v:=b.(type) {
    //	case string:
    //		fmt.Println("我是字符串")
    //		fmt.Println(v)
    //	case int:
    //		fmt.Println("我是int")
    //		fmt.Println(v)
    //	case [3]int:
    //		fmt.Println("我是数组")
    //		fmt.Println(v)
    //	}
    //}
	// 使用
    //var a int=10
    //var b string="lqz"
    //var c [3]int
    //var e Empty  //空接口类型
    //e=a
    //e=b
    //e=c
    //fmt.Println(e)
    //tes3(a)
    //tes3(b)
    //tes3(c)

    // 6、匿名空接口，没有名字的空接口  一般用在形参上
    //func tes4(b interface{})  {
    //	fmt.Println(b)
    //}
	// 使用
    //tes4(111)
    //tes4("111")
    //d := PDuck{name: "hhhh"}
    //tes4(d)
	
	// 7、
    //var a[3]Duck
    //a[1]=PDuck{}
    //a[2]=TDuck{}
    //var b map[string]interface{}= make(map[string]interface{})
    //b["name"]="lqz"
    //b["age"]=19
    //b["duck"]=PDuck{}
    //fmt.Println(a)
    //fmt.Println(b)
	
```

* 接口高级
* 空接口的应用
* 1、空接口作为函数的参数
* 2、空接口作为map的值
* 一个接口的值（简称接口值）是由一个具体类型和具体类型的值两部分组成的。这两部分分别称为接口的动态类型和动态值。
```go
    // 1、 实现多个接口
    // 定义一个鸭子接口，Speak，Run方法
    //type Duck interface {
    //	Speak()
    //	Run()
    //}
    //type Animal interface {
    //	eat()
    //	sleep()
    //}
    //// 普通鸭子
    //type PDuck struct {
    //	name string
    //}
    //// 唐老鸭
    //type TDuck struct {
    //	name string
    //	age int
    //}
    //// 实现Duck接口
    //func (p PDuck) Speak()  {
    //	fmt.Println("普通鸭子嘎嘎叫")
    //}
    //func (p PDuck) Run()  {
    //	fmt.Println("普通鸭子走")
    //}
    //func (p TDuck) Speak()  {
    //	fmt.Println("唐老鸭说人话")
    //}
    //func (p TDuck) Run()  {
    //	fmt.Println("唐老鸭跑路")
    //}
    ////唐老鸭实现Animal接口
    //func (p TDuck)sleep()  {
    //	fmt.Println("唐老鸭睡觉",p.name)
    //}
    //func (p TDuck)eat()  {
    //	fmt.Println("唐老鸭吃东西",p.name)
    //}
	// 使用
    //var t TDuck=TDuck{}
    //var a Animal
    //var d Duck
    ////一旦转到某个接口上，只能使用接口的方法，自身属性和自身方法需要类型断言后才能使用
    //a=t
    //a.sleep()     //Animal的方法
    //a.eat()       //Animal的方法
    //d=t
    //d.Speak()     //Duck的方法
    //d.Run()       //Duck的方法

    ////2 接口嵌套
    //type Animal interface {
    //	eat()
    //}
    //type Duck interface {
    //	Animal	// 嵌套
    //	speak()
    //}
    ////如果一个结构体实现duck接口
    //type PDuck struct {
    //	name string
    //}
    //func (p PDuck)speak()  {
    //}
    //func (p PDuck)eat()  {
    //}
	
	// 接口的零值
    //var a Animal
    //fmt.Println(a)    // <nil>    是引用类型
```
---
#### 自定义集合类型
```go
    //定义MySet类型
    type MySet map[interface{}]bool
    //判断元素是否存在
    func (m MySet) isExist(a interface{}) bool {
        return m[a]
    }
    //返回set长度
    func (m MySet) len() int {
        return len(m)
    }
    //设置值
    func (m MySet) set(a interface{}) {
        m[a] = true
    }
    //删除值
    func (m MySet) delete(a interface{}) {
        delete(m, a)
    }
	
	// 测试
	//创建一个set
	var a MySet = make(MySet)
    //相当于
    //var a MySet = make(map[interface{}]bool)
    //打印set的长度
    fmt.Println(a.len())
    //放入一个值
    a.set(1)
    //放入一个相同值
    a.set(1)
    a.set("fanghao")
    a.set("fanghao")
    a.set("fanghao")
    a.set("fanghao22")
    a.set("fanghao22")
    a.set("fanghao2222")
    //打印长度，还是1
    //fmt.Println(a.len())
    //判断1是否存在
    //fmt.Println(a.isExist(2))
    ////删除1
    a.delete(1)
    ////判断1是否存在
    fmt.Println(a.isExist(1))
    fmt.Println(a.len())
    
    for i,_:=range a{
    fmt.Println(i)
    }
    

```

#### 补充，make 和 new的区别

* Go语言中的内建函数new和make是两个用于内存分配的原语（allocation primitives）。ew只分配内存，make用于slice，map，和channel的初始化。
* new用来初始化变量并分配内存。它的第一个参数是一个类型，不是一个值，它的返回值是一个指向新分配类型零值的指针。
  channel, func, map, slice等零值是nil。
* 关于内置函数 make，官方的介绍是 make 内置函数仅用作分配内存空间并初始化 slice，map 和 chan 类型的对象。
  与 new 相同，第一个参数是类型，而不是值。与 new 不同，make 的返回类型与其参数的类型相同，而不是指向它的指针。
  `func make(t Type, size ...IntegerType) Type`
  返回值取决于传参的类型：
* Slice
  `s := make([]T, 0, 10)`
  以上示例代码表示分配一个长度为 10 的底层数组，返回一个长度为 0，容量为 10 的切片。
  使用内置函数 make 初始化 slice，第一个参数是类型，第二个参数是 slice 的长度，第三个参数是可选参数，它代表 slice 的容量，如果不传入第三个参数，slice 的容量与长度相同，但是如果传入第三个参数，它的值（容量）比如大于或等于传入的第二个参数（长度）。

* Map
  `m := make(map[T]T)`
  以上示例代码表示给 map 分配内存空间。
  使用内置函数 make 初始化 map，传入的参数是类型，map 没有容量限制，初始化时无需指定容量的大小。

* Channel
  `c := make(chan T, 10)`
  以上示例代码表示给 channel 分配的内存空间大小（缓冲容量）为 10。channel 的缓冲区使用指定的值初始化缓冲容量。如果为零或忽略大小(不传入第二个参数)，则 channel 为无缓冲的。


##### new
关于内置函数 new，官方介绍是内置函数 new 仅用作分配内存空间，第一个参数是类型，而不是值，返回值是指向新分配该类型的零值的指针。

`func new(Type) *Type`
在 Golang 开发中，通常不太常用内置函数 new，它的使用场景一般是需要显式返回指针。
* 这是一个用来分配内存的内建函数，但是与C++不一样的是，它并不初始化内存，只是将其置零。
* 也就是说，new(T)会为T类型的新项目，分配被置零的存储，并且返回它的地址，一个类型为*T的值。在Go的术语中，其返回一个指向新分配的类型为T的指针，这个指针指向的内容的值为零（zero value）。注意并不是指针为零。

* 小结
* make 仅用于初始化 slice，map 和 chan，new 可用于初始化任意类型。
* make 返回值是”引用类型“，new 返回值是指针类型。


#### 结构体取代类
* Go 不支持类，而是提供了[结构体]。结构体中可以添加[方法]。这样可以将数据和操作数据的方法绑定在一起，实现与类相似的效果。
```go
    // 定义
    //创建命名的结构体
    type Person struct {
        Name string
        Age int
        Sex string
    }
    
    func New(name string,age int,sex string) Person {
        return Person{name,age,sex}
    }
    
    func (p Person)PrintName()  {
        fmt.Println(p.Name)
    }
	
	// main函数
	per :=person.New("lqz",19,"男")  // 类似实例化，使用绑定方法new创建

    //var per Person = new Person("lqz",19,"男")
    fmt.Println(per)
    per.PrintName()

```


### 7、并发
* Go 编程语言原生支持并发。Go 使用 Go 协程（Goroutine） 和信道（Channel）来处理并发。
```python
并发（concurrency）和并行（parallellism）是：
    解释一：并行是指两个或者多个事件在同一时刻发生；而并发是指两个或多个事件在同一时间间隔发生。
    解释二：并行是在不同实体上的多个事件，并发是在同一实体上的多个事件。
    解释三：并行是在多台处理器上同时处理多个任务。如 hadoop 分布式集群，并发是在一台处理器上“同时”处理多个任务。
    所以并发编程的目标是充分的利用处理器的每一个核，以达到最高的处理性能。

并行(parallel)：指在同一时刻，有多条指令在多个处理器上同时执行。所以无论从微观还是从宏观来看，二者都是一起执行的。

并发(concurrency)：指在同一时刻只能有一条指令执行，但多个进程指令被快速的轮换执行，使得在宏观上具有多个进程同时执行的效果
但在微观上并不是同时执行的，只是把时间分成若干段，使多个进程快速交替的执行。

```
```go
并发：同一时间段内执行多个任务（你在用微信和两个女朋友聊天）。
并行：同一时刻执行多个任务（你和你朋友都在用微信和女朋友聊天）。

Go语言的并发通过goroutine实现。goroutine类似于线程，属于用户态的线程，我们可以根据需要创建成千上万个goroutine并发工作。
    goroutine是由Go语言的运行时（runtime）调度完成，而线程是由操作系统调度完成。
Go语言还提供channel在多个goroutine间进行通信。goroutine和channel是 Go 语言秉承的 CSP（Communicating Sequential Process）并发模式的重要实现基础。
```

### 8、GO协程（goruntine）
* goroutine的概念类似于线程，但 goroutine是由Go的运行时（runtime）调度和管理的。Go程序会智能地将 goroutine 中的任务合理地分配给每个CPU。Go语言之所以被称为现代化的编程语言，就是因为它在语言层面已经内置了调度和上下文切换的机制。
* Go 语言通过编译器运行时（runtime），从语言上支持了并发的特性。Go 语言的并发通过 goroutine 特性完成。goroutine 类似于线程，但是可以根据需要创建多个 goroutine 并发工作。goroutine 是由 Go 语言的运行时调度完成，而线程是由操作系统调度完成。
* OS线程（操作系统线程）一般都有固定的**栈内存（通常为2MB）**,一个goroutine的栈在其生命周期开始时只有**很小的栈（典型情况下2KB）**，goroutine的栈不是固定的，他可以按需增大和缩小
* **使用**,Go语言中使用goroutine非常简单，只需要在调用函数的时候在前面加上`go`关键字，就可以为一个函数创建一个goroutine。
* 一个goroutine必定对应一个函数，可以创建多个goroutine去执行相同的函数。
```
//goroutine--->协程---2kb大小，100
//线程----》几个m
//go协程会复用线程
// goroutine之间通信，通过 信道channel 通信
//go推崇用信道通信，而不推崇用共享变量通信（锁，死锁）
```
* goroutine的优势(协程相比于线程的优势)
```
相比线程而言，Go 协程的成本极低。堆栈大小只有若干 kb，并且可以根据应用的需求进行增减。而线程必须指定堆栈的大小，其堆栈是固定不变的。
Go 协程会复用（Multiplex）数量更少的 OS 线程。即使程序有数以千计的 Go 协程，也可能只有一个线程。如果该线程中的某一 Go 协程发生了阻塞（比如说等待用户输入），那么系统会再创建一个 OS 线程，并把其余 Go 协程都移动到这个新的 OS 线程。所有这一切都在运行时进行，作为程序员，我们没有直接面临这些复杂的细节，而是有一个简洁的 API 来处理并发。
Go 协程使用信道（Channel）来进行通信。信道用于防止多个协程访问共享内存时发生竞态条件（Race Condition）。信道可以看作是 Go 协程之间通信的管道。我们会在下一教程详细讨论信道。
```

* **GMP模型**(GPM)
* GPM是Go语言运行时（runtime）层面的实现，是go语言自己实现的一套调度系统。区别于操作系统调度OS线程。

```
    -G很好理解，就是个goroutine的，里面除了存放本goroutine信息外 还有与所在P的绑定等信息。
    -P管理着一组goroutine队列，P里面会存储当前goroutine运行的上下文环境（函数指针，堆栈地址及地址边界），
        P会对自己管理的goroutine队列做一些调度（比如把占用CPU时间较长的goroutine暂停、运行后续的goroutine等等）当自己的队列消费完了就去全局队列里取，如果全局队列里也消费完了会去其他P的队列里抢任务。
    -M（machine）是Go运行时（runtime）对操作系统内核线程的虚拟， M与内核线程一般是一一映射的关系， 一个groutine最终是要放到M上执行的；

    P与M一般也是一一对应的。他们关系是： P管理着一组G挂载在M上运行。
        当一个G长久阻塞在一个M上时，runtime会新建一个M，阻塞G所在的P会把其他的G 挂载在新建的M上。
        当旧的G阻塞完成或者认为其已经死掉时 回收旧的M。

    P的个数是通过runtime.GOMAXPROCS设定（最大256），Go1.5版本之后默认为物理线程数。 
        在并发量大的时候会增加一些P和M，但不会太多，切换太频繁的话得不偿失。

    单从线程调度讲，Go语言相比起其他语言的优势在于OS线程是由OS内核来调度的，
        goroutine则是由Go运行时（runtime）自己的调度器调度的，
        这个调度器使用一个称为m:n调度的技术（复用/调度m个goroutine到n个OS线程）。 
        其一大特点是goroutine的调度是在用户态下完成的， 不涉及内核态与用户态之间的频繁切换，
        包括内存的分配与释放，都是在用户态维护着一块大的内存池， 不直接调用系统的malloc函数（除非内存池需要改变），
        成本比调度OS线程低很多。 另一方面充分利用了多核的硬件资源，近似的把若干goroutine均分在物理线程上，
        再加上本身goroutine的超轻量，以上种种保证了go调度方面的性能。
```

* **GOMAXPROCS**
```go
    Go运行时的调度器使用GOMAXPROCS参数来确定需要使用多少个OS线程来同时执行Go代码。默认值是机器上的CPU核心数。
    Go1.5版本之前，默认使用的是单核心执行。Go1.5版本之后，默认使用全部的CPU逻辑核心数。
    
    //设置P的大小，认为是cpu核数即可
	runtime.GOMAXPROCS(6)
	fmt.Println("主线程开始执行")
	go func() {for  {fmt.Println("xxxx")}}()
	time.Sleep(10*time.Second)
	fmt.Println("主线程结束执行")
```


* Go语言中的操作系统线程和goroutine的关系：
```
    一个操作系统线程对应用户态多个goroutine。
    go程序可以同时使用多个操作系统线程。
    goroutine和OS线程是多对多的关系，即m:n。(用户线程和操作系统线程)
```

### 9、信道**channel**

* Go语言的并发模型是CSP（Communicating Sequential Processes），提倡通过通信共享内存而不是通过共享内存而实现通信。
* Go 语言中的通道（channel）是一种特殊的类型。通道像一个传送带或者队列，总是遵循先入先出（First In First Out）的规则，保证收发数据的顺序。每一个通道都是一个具体类型的导管，也就是声明channel的时候需要为其指定元素类型。

* channel是一种类型，一种引用类型。声明通道类型的格式如下：
```
    var 变量 chan 元素类型
    var ch1 chan int   // 声明一个传递整型的通道
    var ch2 chan bool  // 声明一个传递布尔型的通道
    var ch3 chan []int // 声明一个传递int切片的通道
```
* 创建channel
* 通道是引用类型，通道类型的空值是nil。声明的通道后需要使用make函数初始化之后才能使用。
* 当做参数传递时，不需要取地址，改的就是原来的
```
    make(chan 元素类型, [缓冲大小])     // channel的缓冲大小是可选的。
    ch4 := make(chan int)
    ch5 := make(chan bool)
    ch6 := make(chan []int)
```

* channel操作
通道有发送（send）、接收(receive）和关闭（close）三种操作。
发送和接收都使用<-符号。
```go
    // 1、定义
    ch := make(chan int)
    // 2、放值(发送)
	ch <- 100
	// 3、取值（接收）
    x := <- ch // 从ch中接收值并赋值给变量x
    <-ch       // 从ch中接收值，忽略结果
	// 4、关闭
	//我们通过调用内置的close函数来关闭通道。
	close(ch)
```
* 无缓冲的通道
发送和接受必须都要有，只有一方都会发生死锁（能通过编译，但是执行会报错，如下）
使用无缓冲通道进行通信将导致发送和接收的goroutine同步化。因此，无缓冲通道也被称为同步通道。
```go
	ch := make(chan int)
    //ch <- 10      // 只放置
    <- ch           //不放置，只取
    fmt.Println("发送成功")
```
* 有缓冲的通道
只要通道的容量大于零(无缓冲信道数字是0)，那么该通道就是有缓冲的通道，通道的容量表示通道中能存放元素的数量。
```go
	ch := make(chan int, 1)
    ch <- 10 
    fmt.Println("发送成功")
	
	// 2、
    var c chan int =make(chan int,2)  //无缓冲信道数字是0
    c<-1
    c<-2
    //c<-7  //死锁
    <-c
    <-c
    //<-c // 取空了，死锁（一个goroutine中会出现）
```
* for range从通道循环取值
* for循环循环信道，如果不关闭会报死锁，如果关闭了，放不进去，循环结束
```go
	ch1,ch2 := make(chan int),make(chan int)
    // 开启goroutine将0~10的数发送到ch1中
    go func() {
    	for i := 1; i < 10; i++ {ch1 <- i}
    	close(ch1)}()
    // 开启goroutine从ch1中接收值，并将该值的平方发送到ch2中
    go func() {
    	for {i, ok := <-ch1 // 通道关闭后再取值ok=false
    		if !ok {break}
    		ch2 <- i * i}
    	close(ch2)}()
    // 在主goroutine中从ch2中接收值打印
    for i := range ch2 { // 通道关闭后会退出for range循环
    	fmt.Println(i)
    }
```
* 长度和容量
我们可以使用内置的**`len`函数**获取通道内元素的数量，使用**`cap`函数**获取通道的容量

* 单向信道
* `chan<- int`是一个**只写**单向通道（只能对其写入int类型值），可以对其执行发送操作但是**不能执行接收**操作；
* `<-chan int`是一个**只读**单向通道（只能从其读取int类型值），可以对其执行接收操作但是**不能执行发送**操作。
```go
    func sendData(sendch chan<- int) {
        sendch <- 10
    }
```

* **worker pool**（goroutine池）
在工作中我们通常会使用可以指定启动的goroutine数量–worker pool模式，控制goroutine的数量，防止goroutine泄漏和暴涨。

* 注意事项
```
  发送与接收默认是阻塞的。这是什么意思？当把数据发送到信道时，程序控制会在发送数据的语句处发生阻塞，直到有其它 Go 协程从信道读取到数据，才会解除阻塞。与此类似，当读取信道的数据时，如果没有其它的协程把数据写入到这个信道，那么读取过程就会一直阻塞着。
  关于关闭通道需要注意的事情是，只有在通知接收方goroutine所有的数据都发送完毕的时候才需要关闭通道。
  通道是可以被垃圾回收机制回收的，它和关闭文件是不一样的，在结束操作之后关闭文件是必须要做的，但关闭通道不是必须的。
  关闭后的通道有以下特点：
  对一个关闭的通道再发送值就会导致panic。
  对一个关闭的通道进行接收会一直获取值直到通道为空。
  对一个关闭的并且没有值的通道执行接收操作会得到对应类型的零值。
  关闭一个已经关闭的通道会导致panic（主动抛出异常）。
 ```

### **select**多路复用
```
select 语句用于在多个发送/接收信道操作中进行选择。
select 语句会一直阻塞，直到发送/接收操作准备就绪。
如果有多个信道操作准备完毕，select 会随机地选取其中之一执行。
该语法与 switch 类似，所不同的是，这里的每个 case 语句都是信道操作。
```
```go
    // 1、基本使用
    output1 := make(chan string)
    output2 := make(chan string)
    go func(ch chan string) {		// 匿名函数server1
    	time.Sleep(6 * time.Second)
    	ch <- "from server1"}(output1)
    go func(ch chan string) {		// 匿名函数server2
    	time.Sleep(3 * time.Second)
    	ch <- "from server2"}(output2)
    select {
    case s1 := <-output1:
    	fmt.Println(s1)
    case s2 := <-output2:
    	fmt.Println(s2)
    default:        //2、默认情况
    	// 可以干其他事，模拟非阻塞式io
    	fmt.Println("no value received")
    }
	
	// 2、默认情况，如上
    default:
        // 可以干其他事，模拟非阻塞式io
        fmt.Println("no value received")
    
    // 3、死锁与默认情况：由于没有 Go 协程向该信道写入数据，因此 select 语句会一直阻塞，导致死锁。
	ch := make(chan string)
	select {
        case <-ch:
		//default:      //如果存在默认情况，就不会发生死锁，因为在没有其他 case 准备就绪时，会执行默认情况。
		//    fmt.Println("default case executed")
        //}
    }
	
	// 4、随机选取：如果多个case同时满足，select会随机选择一个。
    output1 := make(chan string)
    output2 := make(chan string)
    go func(ch chan string) {		// 匿名函数server1
    	ch <- "from server1"}(output1)
    go func(ch chan string) {		// 匿名函数server2
    	ch <- "from server2"}(output2)
    time.Sleep(1 * time.Second)
    select {
    case s1 := <-output1:
    	fmt.Println(s1)
    case s2 := <-output2:
    	fmt.Println(s2)
    }
	
	// 5、空 select：select 语句没有任何 case，因此它会一直阻塞，导致死锁。
	select {}
```

### **mutex**(并发安全和锁)
* **临界区**（Critical Section）的概念。当程序并发地运行时，多个 Go 协程不应该同时访问那些修改共享资源的代码。这些修改共享资源的代码称为临界区。
* 使用锁的场景：多个goroutine通过共享内存在实现数据通信
* 有时候在Go代码中可能会存在多个goroutine同时操作一个资源（临界区），这种情况会发生**竞态问题（数据竞态）**
* 如果在任意时刻只允许一个 Go 协程访问临界区，那么就可以避免竞态条件。而使用 Mutex 可以达到这个目的
```go
    var x  = 0  //要放在全局，各个goroutine都可以拿到并且操作
	var w sync.WaitGroup
	var m sync.Mutex  //是个值类型，函数传递需要传地址
	//fmt.Println(m)  //{0 0}
	for i := 0; i < 1000; i++ {
		w.Add(1)
		go func(wg *sync.WaitGroup,m *sync.Mutex) {
			m.Lock()
			x = x + 1
			m.Unlock()
			wg.Done()
		}(&w,&m)
	}
	w.Wait()
	fmt.Println("final value of x", x)
```
* 通过信道来做
```go
    var x  = 0  //要放在全局，各个goroutine都可以拿到并且操作
	var w sync.WaitGroup
	ch := make(chan bool, 1)  //定义了一个有缓存大小为1的信道
	for i := 0; i < 1000; i++ {
		w.Add(1)
		go func(wg *sync.WaitGroup, ch chan bool) {
			ch <- true  // 缓冲信道放满了，就会阻塞
			x = x + 1
			<- ch
			wg.Done()
		}(&w, ch)
	}
	w.Wait()
	fmt.Println("final value of x", x)
```
* **WaitGroup** (等待所有goroutine执行完成)
```go

    var wg sync.WaitGroup   //没有初始化，值类型，当做参数传递，需要取地址
    //fmt.Println(wg)
    for i:=0;i<10;i++ {
        wg.Add(1) //启动一个goroutine，add加1
        go func(i int,wg *sync.WaitGroup)  {    // 匿名函数
            fmt.Println("started Goroutine ", i)
            time.Sleep(2 * time.Second)
            fmt.Printf("Goroutine %d ended\n", i)
            //一旦有一个完成，减一
            wg.Done()
        }(i,&wg)
    }
    wg.Wait() // 一直阻塞在这，直到调用了10个done，计数器减到零

```

* Mutex vs 信道
  1、不同goroutine之间传递数据：共享变量，  通过信道
  2、如果是修改共享变量，建议加锁
  3、如果是协程之间通信，用信道


### 异常处理
* defer:延迟执行,并且即便程序出现严重错误，也会执行
```go
	defer fmt.Println("我最后执行")  //注册一下，并不执行，等main函数执行完了以后，从下往上执行defer定义的东西
	defer fmt.Println("我倒数第二个打印")
	fmt.Println("我先执行")
	//var a []int
	//fmt.Println(a[10])
```
* panic：主动抛出异常 raise
* recover：恢复程序，继续执行
```go
  defer func() {
      if error:=recover();error!=nil{
          //except的东西
          fmt.Println(error)
      }
      //相当于finally，无论是否出错，都会执行
  }()
  可能会错误的代码

```

```go

    //实例
    //定义三个函数
    func f1(){
      fmt.Println("f1 f1")
    }
    func f2(){
      defer func() {   //这个匿名函数永远会执行
          //error:=recover()  //恢复程序继续执行
          //fmt.Println(error) //如果没有错误，执行recover会返回nil    如果有错误，，执行recover会放错误信息
          if error:=recover();error!=nil{
              //表示出错了，打印一下错误信息，程序恢复了，继续执行
              fmt.Println(error)
          }
          // 相当于finally
          fmt.Println("我永远会执行，不管是否出错")
      }()
      fmt.Println("f2 f2")
      //panic("主动抛出错误")
    }
    func f3(){
      fmt.Println("f3 f3")
    }
    
    //main函数
    f1()
    f2()
    f3()
```
```go

	f, err := os.Open("/test.txt")
	if err != nil {     // 单独处理每一个错误
		fmt.Println(err)
		return
	}
	if err != nil {     // 单独处理每一个错误
		fmt.Println(err)
		return
	}
	fmt.Println(f.Name(), "opened successfully")
```














