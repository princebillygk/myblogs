---
layout: collection_item
title:  "Kotlin Learning"
category: kotlin
tags: kotlin
---

### Table of contents
* TOC
{:toc}

<br><br><br>

# How you should learn kotlin?

* If you are a python programmer you must make use of **[Khan Academy kotlin course (text based)](https://khan.github.io/kotlin-for-python-developers/)** - I really get helped from it.
* **[Go through the codelab courses](https://developer.android.com/courses/basic-android-kotlin-training/overview)** - you can skip the android specific courses for now. if you are video guy then this **[Udacity bootcamp in kotlin by google](https://classroom.udacity.com/courses/ud9011)** is the equavalent of the textbase kotlin bootcamp codelab course.
* Here's the official website **[documentation](https://kotlinlang.org/docs/reference/)** - at least go through once
* And last but not least revision this blog every time you start your new project

if you are into competitive programming you can also read this **[article](https://kotlinlang.org/docs/tutorials/competitive-programming.html)** from official website.


<br><br><br>
## Variable
* **Run time constant**: Variables that which can be **assigned only once**
    ```kotlin
val firstname = "Prince Billy Graham"
    ```
* Variable which can be assigned any number of times
    ```kotlin
var age = 22
++ age
    ```

<br><br><br>

## Compile time / top level Constant
You can declare compile time constant variable using `const val` keyword:
```kotlin
const val pi = 3.1416
```
it has to be declared at the top (not enclosed inside a block).

<br><br><br>

## Datatype
### Numeric
#### Make numbers more readable by using underscores:
```kotlin
val oneBillion = 1_000_000_000L
val ssn = 999_99_9999L 
val hexBytes = 0xFF_CC_DE_5E // hexadecimal
val bytes = 0b1110101_100010_1010101
```

### Characters
enclosed inside single quote `''`

### String
#### String literal:
There are two types of string literal in kotlin.
* **Escaped String**: Can process escaped characters. enclosed inside double quote `" "`. eg. `"Hi, How are you?\n"`
* **Raw String**: Can contain any characters including new line. cannot process escape sequnce. enclosed inside `""" """`.
    ```
"""
    Hello World
    Hello Kity
"""
    ```

#### Template Expression
```kotlin
var name = "princebilly"
println("My Name is $name")
println("2 + 2 = ${2 + 2}")
```

<br><br><br>

## Different Types of Range and progressions in kotlin
### `1..10`
**values:** 1, 2, 3, 4, 5, 6, 7, 8, 9, 10<br>
**description:** includes all number from 1 to 10. This range always moves forward (in fact 10..1 will include no values)

### `10 downTo 1`
**values:** 10, 9, 8, 7, 6, 5, 4, 3, 2, 1<br>
**description**: includes all number from 1 to 10 but in backwards. This range always moves backward

### `1 until 10` 
**values:** 1, 2, 3, 4, 5, 6, 7, 8, 9<br>
**description:** includes all number from 1 to 10 - 1 or 9. this range always moves forward

### Using `step` keyword at the end of `x downTo y` / `x..y` / `x unlitl y`
using step keyword we can tell kotlin to move in specific number of step instead of 1 step
```kotlin
1..10 step 2            // 1, 3, 5, 7, 9
10 down 1 step 3        // 10, 8, 6, 4, 2
3 until 30 step 3       //3, 6, 9, 12, 15, 18, 21, 24, 27
```
<br><br><br>

### Nullability:
We can allow a variable to be null using `?` at the end of the variable name:
```kotlin
var number: Int? = null
```
#### Null Safety operators:
##### Elvis operator: 
```kotlin
val x = b?: 10
```
**description**: if b is not null then use it otherwise, assign 10 to x

##### Safe call operator:
```
val name = person?.ready { "$firstName $lastName"}
```
**description**: if person is not null then call ready function and return the name otherwise (when the person is null) return null

##### Null assertion operator:
**last but not least** stop the program if the variable is null and give and Exception
```
val name = person!!.readdy {"$firstname $lastName"}
```
<small style="color: #0d47a1; text-style: bold">Sometime you can use it to make the linter and compiler happy when you are sure that the value is not null but the program doesn't know.</small>


<br><br><br>


## Function
### One line function example:
```kotlin
fun start(): String = "OK"
fun start() = "OK" // type is optinal here it will get automatically infered
```
### Supports default Argument
```kotlin 
fun functionWithDefaultArg(arg1: String, defaultArg1: Int = 0, defaultArg2:Boolean = false) {
    ...
}
```


<br><br><br>


## Lambda Function
* lambda function syntax
    ```kotlin
{var1, var2-> var1 * var2}
{() -> prinln("lambda function with no parameters")} 
{ it % 2 == 0} // the default single param is it
{
    prinln("Multiline")
    prinln("lambda")
    prinln("function")
    "Hello World" // the last expression will be the return value
}
    ```

* We don't need to put lambda function in first brackets if we are passing it as last parameter to a higher order function
    ```kotlin
// collection.any is the higher order function
//and we are passing a lamba function in it
fun anyEven(collection: Collection<Int>) = collection.any { it % 2 == 0}
    ```

<br><br><br>


## List
* **MutableList**: Can be modified after the creation
*  **List**: Cannot be modified after the creation
<br>
Example: `val numbers = listOf(1, 2, 3, 4, 5, 6)`

### Accessing list item:
* **Using get function**: `numbers.get(0) // 1`
*  **Using index**: `numbers[0] //1`
*  **Getting the first item:** `numbers[0]`, `numbers.first()`, `numbers.get(0)`
*  **Getting the last item**: `numbers[numbers.size - 1]`, `number.last()`. `numbers.get(numbers.size - 1)`

### Check if an item is available in the list:
```kotlin
numbers.contains(4) //true
numbers.contains(7) //false
```
### Add item(s) to mutable list:
```kotlin
var colors = mutableListOf("purple", "green", "orange")
```
* **Adding a single item**:  `colors.add("blue")`
* **Adding a multiple items**: `colors.addAll("yellow", "red", "white")`

### Removing items:
* **Removing a item using value:**
    ```kotlin
    // Removing an item that exits will return true  
    colors.remove("red") // true
    // Removing an item that doesn't exist will return false
    color.remove("black") //false
    ```
* **Removing a item using index:** `colors.removeAt(0)`
* **Remove all items:** `colors.clear()`

### Some important functions:
```kotlin
val colors = listOf ("Red", "Green", "Blue")
colors.isEmpty() // check if a list is empty : false
colors.reversed() // returns the list in reversed form : ["Blue", "Green", "Red"]
colors.sorted() // returns the list in sorted from ["Blue", "Green", "Red"]
/*
```

#### Joining array of strings:
Take a look at the function definition first
```kotlin
fun joinToString(
    separator: String = ", ",
    prefix: String = "", 
    postfix: String = "",
): String
```
**Example:**
```kotlin
colors.joinToString() // returns "Red, Green, Blue" 
colors.joinToString("+", "[", "]") // returns "[Red+Green+Blue]"
```

<br><br><br>

## Array
Array is only non mutable.
Declaring a array:
```kotlin
val names = arrayOf("Prince", "Billy", "Graham") // "Prince", "Billy", "Graham"

val numbers = Array(5) {it} // 0, 1, 2, 3, 4
//here "it" is the passed argment which is the index of each item
val squareOfNumbers = Array(5) {it * it} // 0, 1, 4, 9, 16
```
<br><br><br>


##  Conditional Statement
### if, else if, else
Not anything new about this. 
### Ternary Condition / On liner if-else
 **you can use if else like a ternary condition**
```
val number = 345
val numberType = if (number % 2 == 1) "Odd" else "Even"
```

<br><br><br>

## Switch statement alternative / When statement

<br><br><br>

## Loops
### For loops
#### iterating through collections
```
var myList = listOf("COD", "IGI", "PUBG" )
```
**Without Index**:
```kotlin
for (i in myList) {
    println(i)
}
```
**With index**: 
withIndex() function returns a [IndexedValue](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-indexed-value/) object
```kotlin
for (i in myList.withIndex()) {
    println("index: ${i.index} => item ${i.value}") 
}

// after destructing pair
for ((index, item) in myList.withIndex()) {
    println("index: $index => item ${item}")
}
```
#### Iterating through different types range
```kotlin
// .. range
for (i in 1..10) {
    println(i)
}
// until
for (i in 1 until 10) {
    println(i)
}
// downTo
for (i in 10 downTo 1) {
    println(i)
}

// .. with step
for (i in 1..10 step 3) {
    println(i)
}
// unitl with step
for (i in 1 until 10 step 2) {
    println(i)
}
// downTo with step
for (i in 20 downTo 1 step 4) {
    println(i)
}
```
<br>

### Repeat Loop
```kotlin
repeat(10) {
    println("Hello World")
}
```
<small style="color: gray">Prints "Hello World\n" in 10 times</small>

repeat function also passes the index to the passed function

```kotlin
repeat(10) { index ->
    println("This is index $index")
}
```

<small style="color: gray">This is index 0\n, ..., This is index 9\n</small>

<br>

### While Loop
```
while (money > 1000) {
    money -= 10
}
```

<br>

### Do-while loop
```
do {
    money -= 10
} while (money > 1000)
```
<br><br><br>


