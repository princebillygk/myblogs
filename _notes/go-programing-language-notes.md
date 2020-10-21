---
layout: collection_item
title:  "Go Programning Language Note"
category: Programning
tags: go web api rest
---

## Imports and exports
### Importing single package
```go
import "fmt"
```
## Importing multple package
#### Recommended way

```go 
import {
    "fmt"
    "math/rand"
    }
```
The other way is

```go
import "fmt"
import "math/rand"
```


## Exporting packages
A name begins with capital letter is exported this is why we `fmt.Println` instead of `fmt.println`

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
**When two or more consecutive named paramaters are of same type we can omit type from all except the last parameter.***

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

### Declaring multple var at once 

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

## Basic Types

`bool`,<br> `string` <br>
`int`, `int8`, `int16`, `int32`, `int64` <br>
`uint`, `uint8`, `uint16`, `uint32`, `uint64`, `uintptr` <br>
`byte` alias of `uint8` <br>
`rune` represents unicode point, alias of `int32` <br>
`float32`, `float64` <br>
`complex64`, `complex128` <br>

## Type conversion
Type conversion in go is done by T(v) wher T is the type and v is the value

## Constant 
Constant in typescript can be string boolean or numeric values. Constant can not be declared using := 

```go
const Pi = 3.1416
```
