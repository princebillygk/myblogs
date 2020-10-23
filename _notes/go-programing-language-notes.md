---
layout: collection_item
title:  "Go Programning Language Note"
category: Programning
tags: go web api rest
---

## Imports 
### Importing single package
```go
import "fmt"
```
### Importing multple package
#### Recommended way

```go 
import (
    "fmt"
    "math/rand"
    )
```
The other way is

```go
import "fmt"
import "math/rand"
```

<br><br><br>
## Exporting packages
A name begins with capital letter is exported this is why we `fmt.Println` instead of `fmt.println`

<br><br><br>
## User defined function in go
Example:

```go
package main
import "fmt"

func multiply(x int, y int) int {
  return x * y
}

func main() {
   fmt.Println(multiply(4, 25))
}
```
As in this function x and y are consecutive int paramaters so we can omit type declaration for x.<br>
<div class="info">When two or more consecutive named paramaters are of same type we can omit type from all except the last parameter</div>

```go 
package main 
import "fmt"

func multiply (x , y int) int {
    return x * y
} 

func main() {
    fmt.Println(multiply(4, 25))
}
```

### The damn interest things about go function

#### 1. Multple return values
Have you ever seen any traditional programming language allowing return multiple values from funciton without a object (eg. array, tupple, set...) Bang!!! here is go which allows you to return multiple values from a function

```go
package main

import "fmt"

func main() {
    a := "Hello"
    b := "World"
    a, b = swap(a, b)
    fmt.Println(a, b)
}

func swap (x, y string) (string, string) {
    return y, x
}
```

#### 2. Named return value
* Increase the readability 
* Used to make document of the functon

The named value is recommended when the function returns different types of multple value. For readability it is always better to use named return value. In this case we do not need to explicity say which variable to return. The function will automatically return the named return values but we will still need to include return statment.

```go
package main
import "fmt"

func main() {
    fmt.Println(swap("Hello", "World"))
}

func swap(a, b string) (x, y string) {
    x = b
    y = a
	return
}
```

<br><br><br>
## Variable declaration

```go
var c, python, java bool
var i, j int = 1, 2
var k string = 3
var p int
```

### Shorter syntax
```go
x := 2
i, j := 23, "Hello World"
```

### Declaring multple variable of differnet type at once 

```go
var (
	ToBe   bool       = false
	MaxInt uint64     = 1<<64 - 1
	z      complex128 = cmplx.Sqrt(-5 + 12i)
)
```

variables intialized without value witll be zero value
The zero value is 

```go
    0 //for numeric types
    false //for boolean types
    "" // Empty String for string types
```

<br><br><br>
## Basic Types

`bool`,<br> `string` <br>
`int`, `int8`, `int16`, `int32`, `int64` <br>
`uint`, `uint8`, `uint16`, `uint32`, `uint64`, `uintptr` <br>
`byte` alias of `uint8` <br>
`rune` represents unicode point, alias of `int32` <br>
`float32`, `float64` <br>
`complex64`, `complex128` <br>

## Type conversion
Type conversion in go is done by T(v) where T is the type and v is the value
```go
x int = 4
f float64 = float64(4)
```

## Constant 
Constant in typescript can be string boolean or numeric values. Constant can not be declared using := 

```go
const Pi = 3.1416
```
<br><br><br>
## Loops
### For loop in go
Using shorthand syntax is recommended. 

```go
for i := 0; i < 10; i++ {
	sum += i
}
fmt.Println(sum)
```
### While alternative in Go:
we will use `for` keyword to implement a while loop but this time we will drop the intialization, increment and the semicolons
```go
for sum < 100 {
	sum += sum
}
```
### Some other for loop varialation 
An infinite for loop

```go 
for {
	fmt.Println("Hello World")
}
```

}


### One weird thing about golang
`++` and `--` can only be useable as postfix

```diff
+ x++ //right
- ++x //wrong
+ y-- //right
- --y //wrong
```

<br><br><br>
## If else
If statement condition doesn't need to be surrended by ()

```go
func isOdd(number int) bool {
	if number&1 == 1 {
		return true
	}
	return false
}
```

### The damn interesting thing about go if statement
We can start with a short statement that will be executed before matching the condition

```go
func getRoot(a float64, b float64, c float64) string {
	if d := b*b - 4*a*c; d < 0 {
		fmt.Println(d)
		divider := 2 * a
		imginaryPart := math.Sqrt(-d) / divider
		realPart := -b / divider
		return fmt.Sprintf("x1 = %.3v + %.3vi, x2 = %.3v - %.3vi",
			realPart, imginaryPart, realPart, imginaryPart)
	} else {
		sqrtOfD := math.Sqrt(d)
		x1 := (-b + sqrtOfD) / (2 * a)
		x2 := (-b - sqrtOfD) / (2 * a)
		return fmt.Sprintf("x1 = %.3v, x2 = %.3v", x1, x2)
	}
}
```

if else chain example

```go 
os := runtime.GOOS

if os == "darwin" {
	fmt.Println("OS X. ")
} else if os == "linux" {
	fmt.Println("Linux.")
} else {
	fmt.Printf("%s.\n", os)
}
```

<br><br><br>
## Switch

```go
package main

import (
	"fmt"
	"runtime"
)

func main() {
	fmt.Println("Go runs on ")
	switch os := runtime.GOOS; os {

	case "darwin":
		fmt.Println("OS.X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		fmt.Println("%s\n", os)
	}
}
```
### The damn think about go switch statement 
Go switch statement doesn't need to use break statement of each cases. break is automatic for each cases. Switch statement also supports any type
#### We can use switch as else if chain

```go 
switch t := time.Now(); {
case t.Hour() < 12:
	fmt.Println("Good Morning\n")
case t.Hour() < 17:
	fmt.Println("Good Afternoon\n")
default:
	fmt.Println("Good Evening")
}
```

<br><br><br>

## Defer (Bang!! new concept)
Evaluates but Holds the execution fo statement until the surrounding function return
```go
func main() {
	defer fmt.Println("World")
	fmt.Println("Hello")
}
```
<div class="output">
World
Hello
</div>
### Weird thing about defer
Defer function calls are pushed into stack. First in lastout system
```go
fmt.Println("counting")
for i := 0; i < 10; i++ {
	defer fmt.Println(i)
}
fmt.Println("done")
```
<div class="output">
counting
done
9
8
7
6
5
4
3
2
1
0
</div>
