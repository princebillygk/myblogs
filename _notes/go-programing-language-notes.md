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
A name begins with capital letter is exported this is why we use `fmt.Println` instead of `fmt.println`

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

### Higher-order function

We can use function as argument and return value
```go
package main

import (
	"fmt"
	"math"
)

func compute(fn func(float64, float64) float64) float64 {
	return fn(3, 4)
}

func main() {
	hypot := func(x, y float64) float64 {
		return math.Sqrt(x*x + y*y)
	}
	fmt.Println(hypot(5, 12))
	fmt.Println(compute(hypot))
	fmt.Println((math.Pow))
}
```

## Function closure
A closure is a function valuew that refrence variable from outside of its body.

```go 
package main

import "fmt"

func adder() func(int) {
	sum := 0
	return func(x int) {
		sum += x
		fmt.Println(sum)
	}
}

func main() {
	pos, neg := adder(), adder()
	for i := 0; i < 10; i++ {
		fmt.Println("pos:")
		pos(i) // will change sum variable of its own parent function
		fmt.Println("neg:")
		neg(-2 * i) // will change sum variable  of its own parent function
	}
}
```

An fibonancy generator example using function closure

```go
package main

import "fmt"

func fibonacci() func() int {
	old := 1
	curr := 0
	return func() int {
		temp := curr

		curr = curr + old
		old = temp
		return temp
	}
}

func main() {
	f := fibonacci()

	for i := 0; i < 10; i++ {
		fmt.Println(f())
	}
}
```

<br><br><br>
## Variable declaration

```go
var c, python, java bool
var i, j int = 1, 2
var k string = "Hello World"
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

variables intialized without value will be zero value
The zero value is 

```go
    0 //for numeric types
    false //for boolean types
    "" // Empty String for string types
	nil //for slice
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
Constant in Go programming language can be string boolean or numeric values. Constant can not be declared using := 

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
sum := 1
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

<br><br><br>

## Struct
Struct declaration:

```go
package main

import "fmt"

type Vertex struct {
	X int
	Y int
}

func main() {
	fmt.Println(Vertex{1, 2})
}
```
**accesing struct fields:** We can access struct fields using dot
```go
package main

import "fmt"

type Vertex struct {
	X int
	Y int
}

func main() {
	v := Vertex{1, 2}
	fmt.Printf("%T\n", v)
	fmt.Println(v.X)
	v.X = 4
	fmt.Println(v.X)
}
```

<div class="output">
main.Vertex
1
4
</div>

We can also access struct fields using struct pointer
```go
package main

import "fmt"

type Vertex struct {
	X int
	Y int
}

func main() {
	v := Vertex{1, 2}
	p := &v
	fmt.Printf("%T\n", p)
	p.X = 1e9
	fmt.Println(v)
	fmt.Println(p.Y)    // easy way
	fmt.Println((*p).Y) // cumbersome approch
}
```
### We can explicilty specify which struct field to initialize using {Name: value}

```go
v := Vertex {Y: 0} //here X:0 implicit
v1 := Vertex {} //here X:0 and Y:0
```
One more example to be more cleared
```go 
package main

import "fmt"

type Vertex struct {
	X, Y int
}

var (
	v1 = Vertex{1, 2}
	v2 = Vertex{X: 1}
	v3 = Vertex{}
	p  = &Vertex{1, 2}
)

func main() {
	fmt.Println(v1, p, v2, v3)
}
```
<div class="output">
{1 2} &{1 2} {1 0} {0 0}
</div>


<br><br><br>

## Array
Array is what you already learned in c/c++. Its size is static. In fact array cannot be resized but the way of declaration is little different<br>
`[n]T` Here n is the nubmer of item that the array can hold and T is type

```go 
var a[10]int  // declares a array "a" of 10 items. each item intialized to zero value
```
### We can also intialize array items using {}
```go
primes := [6]int{2, 3, 5, 7, 11, 13}
```

Example:

```go 
package main

import "fmt"

func main() {
	var a [2]string
	a[0] = "Hello"
	a[1] = "World"
	fmt.Println(a[0], a[1])
	fmt.Println(a)

	primes := [6]int{2, 3, 5, 7, 11, 13}
	fmt.Println(primes)
}
```
<div class="info" markdown=1>
###  Another thing that I find a bit weird while coding

```diff
  names := [4]string{
  	"John",
  	"Paul",
  	"Gorge",
- 	"Ringo"
  }
```
<div class="output">
# command-line-arguments
./test.go:10:10: syntax error: unexpected newline, expecting comma or }
</div>
<br>
This code is not ok, but why? we missed a comma at the last element and closed the parenthesis at next line. And this will lead to an error. This error canbe fix by adding a comma(,) after the last item.

```diff
  names := [4]string{
 	"John",
 	"Paul",
 	"Gorge",
+ 	"Ringo",
}
```
</div>

 
<br><br><br>

## Slices

Slices don't have a size limit. Its size is dynamic
We can form a size using ":" from another linear datastructure, or by specifying the values. The [:] range is [start:end - 1]

```
package main

import "fmt"

func main() {
	primes := [6]int{2, 3, 5, 7, 11, 13}
	var even []int = []int{2, 4, 6, 8, 10}
	fmt.Printf("%T\n", even)
	fmt.Println(even)
	var s []int = primes[1:4]

	var q []int = s[2:3]
	fmt.Printf("%T\n", s)
	fmt.Println(s)
	fmt.Printf("%T\n", q)
	fmt.Println(q)
}
```
<div class="info" markdown=1>
The [:] looks like python range but there is a major difference between them. When using [:] to form a slice it doesn't create a new data store, Instead it works like a referece of underlying parent datastructure (eg. array). Infact any change that is done to the slice will also reflect in the underlying array

```go
package main

import "fmt"

func main() {
	names := [4]string{
		"John",
		"Paul",
		"Gorge",
		"Ringo",
	}

	fmt.Println(names)

	a := names[0:2]
	b := names[1:3]
	fmt.Println(a, b)

	b[0] = "XXX"
	fmt.Println(a, b)
	fmt.Println(names)
}
```
<div class="output">
[John Paul Gorge Ringo]
[John Paul] [Paul Gorge]
[John XXX] [XXX Gorge]
[John XXX Gorge Ringo]
</div>

</div>

If we create a slice without slicing a part from an array then. The it will create a array first and then reference it by the slice
```go
package main

import "fmt"

func main() {
	q := []int{2, 3, 5, 7, 11, 13}
	fmt.Println(q)

	r := []bool{true, false, true, true, false, true}
	fmt.Println(r)

	s := []struct {
		i int
		b bool
	}{
		{2, true},
		{3, false},
		{5, true},
		{7, true},
		{11, false},
		{13, false},
	}
	fmt.Println(s)
}
```
<div class="output">
[2 3 5 7 11 13]
[true false true true false true]
[{2 true} {3 false} {5 true} {7 true} {11 false} {13 false}]
</div>

We can ommit the lower bound and the upper bound while slicing

```
package main

import "fmt"

func main() {
	s := []int{2, 3, 5, 7, 11, 13}

	s = s[1:4]
	fmt.Println(s)

	s = s[:2]
	fmt.Println(s)

	s = s[1:]
	fmt.Println(s)

	s = s[:]
	fmt.Println(s)

}
```

<div class="output">
[3 5 7]
[3 5]
[5]
[5]
</div>

<div class="info">The zero value for slice is `nil`</div>

###  We can also make use of builtin make function to created a slice of specific len() and cap() of zeroed array

```go
package main

import "fmt"

func main() {
	a := make([]int, 5)
	printSlice("a", a)

	b := make([]int, 0, 5)
	printSlice("b", b)

	c := b[:2]
	printSlice("c", c)

	d := c[2:5]
	printSlice("d", d)
}

func printSlice(s string, x []int) {
	fmt.Printf("%s len=%d cap=%d %v\n", s, len(x), cap(x), x)
}
```

## Two dimensional example
```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	board := [][]string{
		[]string{"_", "_", "_"},
		[]string{"_", "_", "_"},
		[]string{"_", "_", "_"},
	}

	board[0][0] = "X"
	board[2][2] = "O"
	board[1][2] = "X"
	board[1][0] = "O"
	board[0][2] = "X"

	for i := 0; i < len(board); i++ {
		fmt.Printf("%s\n", strings.Join(board[i], " "))
	}
}
```

<div class="output">
X _ X
O _ X
_ _ O
</div>




### Appending to slice
We can append new item to slice. If the slice doesn't have required capacity it will recreate a new array with new size and refernce it from then.

```go
package main

import "fmt"

func main() {
	var s []int
	printSlice(s)

	s = append(s, 0)
	printSlice(s)

	s = append(s, 1)
	printSlice(s)

	s = append(s, 2, 3, 4)
	printSlice(s)
}

func printSlice(s []int) {
	fmt.Printf("len=%d cap=%d %v %T\n", len(s), cap(s), s, s)
}
```

### Iterating slice using range

The `range` form of the `for` loop iterates over a slice or map. Two values are returned from each iteration. The first one is index and the last one is value

```go
package main

import "fmt"

var pow = []int{1, 2, 4, 8, 16, 32, 64, 128}

func main() {
	for i, v := range pow {
		fmt.Printf("2**%d = %d\n", i, v)
	}
}
```
<div class="output">
2**0 = 1
2**1 = 2
2**2 = 4
2**3 = 8
2**4 = 16
2**5 = 32
2**6 = 64
2**7 = 128
</div>

We can ommit any of index or value by using "\_". Or if we want only index then we can ommit value

```go
package main

import "fmt"

func main() {
	pow := make([]int, 10)
	for i := range pow {
		pow[i] = 1 << uint(i)
	}

	for _, value := range pow {
		fmt.Printf("%d\n", value)
	}
}
```

<div class="output">
1
2
4
8
16
32
64
128
256
512
</div>





<br><br><br>

## Map
<div class="info"> 
0 value of map is nil
</div>
Example:
```go
package main

import "fmt"

type Vertex struct {
	Lat, Long float64
}

var m map[string]Vertex

func main() {
	m = make(map[string]Vertex)
	m["Bell Labs"] = Vertex{
		40.64833, -74.39967,
	}
	fmt.Println(m["Bell Labs"])
}
```
Another Example:
initializing map items:

```go
package main

import "fmt"

type Vertex struct {
	Lat, Long float64
}

var m = map[string]Vertex{
	"Bell Labs": {40.68, -74.3999},
	"Google":    {37.42, -122.08408},
}

func main() {
	fmt.Println(m)
}
```

### Mutating map

```go
package main

import "fmt"

func main() {
	m := make(map[string]int)

	m["Answer"] = 42
	fmt.Println("The value ", m["Answer"])

	m["Answer"] = 48
	fmt.Println("The value ", m["Answer"])

	delete(m, "Answer")
	fmt.Println("The value, ", m["Answer"])

	v, ok := m["Answer"]
	fmt.Println("The value, ", v, "Present? ", ok)
} 
```
<div class="output">
The value  42
The value  48
The value,  0
The value,  0 Present?  false
</div>



## Class alternative in go Method
Method is like regular function but with special receiver argument. A receiver appears in its own argument list between the func keyboard and the method name.




<div class="info">
**One important thing**: Method reciever has to be exist in the same package where we were writting the method. We cannot declare a method with a receiver whose type is defined in another packge (which include build-in types such as float64)
</div>

```go
package main

import (
	"fmt"
	"math"
)

type Vertex struct {
	X, Y float64
}

func (v Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func main() {
	v := Vertex{3, 4}
	fmt.Println(v.Abs())
}
```


We can also modify the reciever argument if we use pointer reciever arugment
```go
package main

import (
	"fmt"
	"math"
)

type Vertex struct {
	X, Y float64
}

func (v Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}

func (v *Vertex) Scale(f float64) {
	v.X = v.X * f
	v.Y = v.Y * f
}

func main() {
	v := Vertex{3, 4}
	v.Scale(10)
	fmt.Println(v.Abs())
}
```

## Choosing a pointer or receiver 

* To modify its receiver value
* Avoid copying large object


## Interfaces

An interface type is defined as a set of method signature

```go
package main

import (
	"fmt"
	"math"
)

type Abser interface {
	Abs() float64
}

func main() {
	var a Abser
	f := MyFloat(-math.Sqrt2)
	v := Vertex{3, 4}

	a = f  // a MyFloat implements absyer
	a = &v // a *Vertex implements

	// In the following line, v is a Vertex (not *Vertex)
	// and doesn't implement Abser
	// a = v

	fmt.Println(a.Abs())
}

type MyFloat float64

func (f MyFloat) Abs() float64 {
	if f < 0 {
		return float64(-f)
	}
	return float64(f)
}

type Vertex struct {
	X, Y float64
}

func (v *Vertex) Abs() float64 {
	return math.Sqrt(v.X*v.X + v.Y*v.Y)
}
```

## EmptyInterface

Generally used with functions that excepts argument of all types

```
package main

import "fmt"

func main() {
	var i interface{}
	describe(i)

	i = 42
	describe(i)

	i = "hello"
	describe(i)
}

func describe(i interface{}) {
	fmt.Printf("(%v, %T)\n", i, i)
}
```



## Type  assertion 
 t := i.(T)

here i is a interface if i is of Type t then it will be asigned to variable to otherwise will generate a panic.
to avoid panic we can also ask to get a second return value, that will tell be true if the type matahes otherwise will return false


```go
package main

import "fmt"

func main() {
	var i interface{} = "hello"

	s := i.(string)
	fmt.Println(s)

	s, ok := i.(string)
	fmt.Println(s, ok)

	f, ok := i.(float64)
	fmt.Println(f, ok)

	f = i.(float64)
	fmt.Println(f)
}
```

## Type switches

```go
package main

import "fmt"

func do(i interface{}) {
	switch v := i.(type) {
	case int:
		fmt.Printf("Twice %v is %v\n", v, v*2)
	case string:
		fmt.Printf("%q is %v bytes long\n", v, len(v))
	default:
		fmt.Printf("I don't know about type %T!\n", v)
	}
}

func main() {
	do(21)
	do("Hello")
	do(true)
}
```


## The Stringer interface `toString` alternative

```go
type Stringer interface {
    String() string
}
```
The fmt package and many others look for this interface to print values

Example: 

```go 
package main

import "fmt"

type IPAddr [4]byte

func main() {
	hosts := map[string]IPAddr{
		"loopback":  {127, 0, 0, 1},
		"googleDNS": {8, 8, 8, 8},
	}

	for name, ip := range hosts {
		fmt.Printf("%v: %v\n", name, ip)
	}
}

func (ip IPAddr) String() string {
	return fmt.Sprintf("%v.%v.%v.%v", ip[0], ip[1], ip[2], ip[3])
}
```
## Errors

```go 
type error interface {
	Error() string
}
```

```go
i, err := strconv.Atoi("42")
if err != nil {
    fmt.Printf("couldn't convert number: %v\n", err)
    return
}
fmt.Println("Converted integer:", i)
```
A nil error denotes success; a non-nil error denotes failure.

```go 
package main

import (
	"fmt"
	"time"
)

type MyError struct {
	When time.Time
	What string
}

func (e *MyError) Error() string {
	return fmt.Sprintf("at %v, %s", e.When, e.What)
}

func run() error {
	return &MyError{
		time.Now(),
		"it didn't work.",
	}
}

func main() {
	if err := run(); err != nil {
		fmt.Println(err)
	}
} 
```
 Another example:

```go
package main

import (
	"fmt"
)

type ErrNegativeSqrt float64

func (e ErrNegativeSqrt) Error() string {
	return fmt.Sprintf("Cannot Sqrt negative number: %v", float64(e))
}

func Sqrt(x float64) (float64, error) {
	if x < 0 {
		return 0, ErrNegativeSqrt(x)
	}
	var z float64 = x / 2
	var prevZ = z

	z = z - (z*z-x)/(2*z)

	for ; prevZ-0.001 < z && z < prevZ-0.001; z -= (z*z - x) / (2 * z) {
		fmt.Println(z)
		prevZ = z
	}
	return z, nil
}

func main() {
	fmt.Println(Sqrt(2))
	fmt.Println(Sqrt(-2))
}

```

## goroutine

`go` keyword is used to create a asynchronous task. function that are called with this keyword will execute asynchronously.

```go
package main

import (
	"fmt"
	"time"
)

func say(s string) {

	for i := 0; i < 5; i++ {
		time.Sleep(100 * time.Millisecond)
		fmt.Println(s)
	}

}

func main() {
	go say("world")
	say("hello")
}
```



### Channel

```
package main

import "fmt"

func sum(s []int, c chan int) {
	sum := 0
	for _, value := range s {
		sum += value
	}
	c <- sum
}

func main() {
	s := []int{7, 2, 8, -9, 4, 0}
	c := make(chan int)
	go sum(s[:len(s)/2], c)
	go sum(s[len(s)/2:], c)
	x, y := <-c, <-c
	fmt.Println(x, y, x+y)
} 
```

### Buffered channel

Overkilling a buffer channel will create a fatal error

```go 
package main

import "fmt"

func main() {
	ch := make(chan int, 2)
	ch <- 1
	ch <- 2
	fmt.Println(<-ch)
	fmt.Println(<-ch)
}
```

## Range and close() channel
```go
package main

import (
	"fmt"
)

func fibonacci(n int, c chan int64) {
	var x, y int64 = 0, 1
	for i := 0; i < n; i++ {

		c <- x
		x, y = y, x+y
	}
	close(c)
}

func main() {
	c := make(chan int64, 50)
	go fibonacci(cap(c), c)
	for i := range c {
		fmt.Println(i)
	}
}
```
## Select 
The select statement lets a goroutine wait on multiple communication operations.

A select blocks until one of its cases can run, then it executes that case. It chooses one at random if multiple are ready.

```go
package main

import "fmt"

func fibonacci(c, quit chan int) {
	x, y := 0, 1
	for {
		select {
		case c <- x:
			x, y = y, x+y

		case <-quit:
			fmt.Println("quit")
			return
		}
	}
}

func main() {
	c := make(chan int)
	quit := make(chan int)
	go func() {
		for i := 0; i < 10; i++ {
			fmt.Println(<-c)
		}
		quit <- 0
	}()
	fibonacci(c, quit)
}
```
Select with default statement

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	tick := time.Tick(100 * time.Milisecond)
	boom := time.After(500 * time.Milisecond)

	for {
		select {
		case <-tick:
			fmt.Println("tick.")
		case <-boom:
			fmt.Println("Boom!")
			return
		default:
			fmt.Println(" ")
			time.Sleep(50 * time.Millisecond)
		}
	}
}
```
## Sycn

Used to avoid channels when we don't need communication among go routine.
So that one go routine access a variable at a time.

```go
package main

import (
	"fmt"
	"sync"
	"time"
)

type SafeCounter struct {
	mu sync.Mutex
	v  map[string]int
}

func (c *SafeCounter) Inc(key string) {
	c.mu.Lock()
	c.v[key]++
	c.mu.Unlock()
}

func (c *SafeCounter) Value(key string) int {
	c.mu.Lock()
	defer c.mu.Unlock()
	return c.v[key]
}

func main() {
	c := SafeCounter{v: make(map[string]int)}
	for i := 0; i < 1000; i++ {
		go c.Inc("somekey")
	}
	time.Sleep(time.Second)
	fmt.Println(c.Value("somekey"))
}
```
