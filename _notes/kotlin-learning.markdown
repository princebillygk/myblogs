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

<div class="info">Sometime you can use it to make the linter and compiler happy when you are sure that the value is not null but the program doesn't know.</div>


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

contains("purple") // false // returns true if contains the item

/* Return part of the list, from the first index up to but not including the second index. */
var shortList = colors.sublist(0, 2) // returns listOf("Red", "Green")
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

## Pair & Triplets
### Pair
* We can declare in two way
    *  using `to` keyword (recommended)
        ```kotlin 
        val pair2 = "age" to 23
        ```
        <div class="info">
        Useful to create map
        </div>
    * using constructor
        ```kotlin
        val pair = Pair("age", 22)
        ```
* The items of property can be accessed by `first` and `second` property
    ```kotlin
    println(pair.first) // "age"
    println(pair.second) // 22
    ```

### Triple
* Contains three items
* Access the property using `first`, `second`, `third`

```kotlin
val triple = Triple("A", "B", "C")
    println(triple.first) // "A"
    println(triple.second) // "B"
    println(triple.third) // "C"
```

<div markdown=1 class="info"> We can destruct pair and triples like any other objects
```
val (item1, item2) = Pair(1, 2)
val (element1, element2, element3) = Triple("A", "B", "C")
```
</div>

<br><br><br>

## Map
Array of key-value pair
### Mutable Map
**Hash Map**: An implementation Mutable Map
```kotlin
val usernames = hashMapOf(
    "google" to "princebillyGK",
    "microsoft" to "Game_pagla",
    "facebook"  to "L1M1T_BR3K3R",
)
println(usernames["google"]) // princebillyGK
```
**Iterating through items:**
```
for ((site, id) in usernames) {
    println("$site: $id")    
}
```
Accessing an key which does not will return **null**
```kotlin
println(usernames["nexuspay"]) // null
println(usernames.get("bkash")) // null
```
Get default value when the key doesn't exist
```kotlin
println(usernames.getOrDefault("bdjobs", "princebillyGK"))
```
Do something else when an key doesn't exist:
```kotlin
var username = usernames.getOrElse("reddit") {
    ...
}
```
**Add new pair**
```
usernames.put("twitter", "tastyCake")
```
putting multiple values
```kotlin
usernames.putAll(mapOf(
    "github" to "user1234",
    "heroku" to "1234user"
))
```
**Remove a pair**
```kotlin
usernames.remove("twitter")
```
## Non mutable map:
same as mutable map but it is non mutable.
```kotlin
val heights = mapOf("Prince" to 5.7, "Liam" to 5.9)
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
```kotlin
when(i) {
    in 1..10 -> println("Between 1 and 10")
    20 -> println("Exact 20")
    15, 16 -> println("15 or 16")
    else -> println("Unknown")
}
```
**When condition with expression inside first parentheses:**
```kotlin
when (x + y) {
    10 -> println("The sum is 10")
    15, 20 -> println("The is sum is 14, 20")
    in 30..35 -> println("The sum is between 30 and 35")
    else -> println("The sum is unknown")
}
```
**Else if chain with when statement:**
```kotlin
when {
    x > y -> println ("X is bigger")
    x > 100 -> println("X is greater than 100")
    x < 5 && y >5 -> println("Perfect")
    else -> println("y is bigger")
}
```
**When statement with inner block:**
```kotlin
when(x) {
    in 100..200 -> {
        println("X is in primary stage")
        println("X is small")
    }
    in 200..300 -> {
        println("X is in secondary stage")
        println("X is medium")
    }
    in 300..400 -> {
        println("X is in final stage")
        println("X is big")
    }
    
}
```



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

## Break & continue
Works as in regular programming language. But here is something to mention we can use label with it in kotlin
### Labeled break and continue
//TODO
<br><br><br>


## Function
Nothing new but here are some noticeable things:
### Compact function example:
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
{() -> println("lambda function with no parameters")} 
{ it % 2 == 0} // the default single param is it
{
    println("Multiline")
    println("lambda")
    println("function")
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

## Inline function 
//TODO
<br><br><br>

## Filter, Map and sequence 
### Regular filter and map
```kotlin
val foods = listOf("Cocacola", "Chatpati", "Orange", "Lemon", "Cabagae", "Ceral", "Chicken", "Potato", "Corn")
    
//filtering
val foodsStartWithC = foods.filter {it[0] == 'C'}
println("Foods Name starts with C: $foodsStartWithC")
/*
Foods Name starts with C: [Cocacola, Chatpati, Cabagae, Ceral, Chicken, Corn]
*/

val foodMapped = foods.map { 
    println("The item $it is accessed")
    it
}
```

### Lazy filter and map

It doesn't evaluates all value immediately instead, evaluates each value when they get accessed.<br>

**Lazy Map**
```kotlin
// lazy filter
val lazyFoodsStartWithC = foods.asSequence().filter {it[0] == 'C'}
println("Foods Name starts with C: $lazyFoodsStartWithC")
```
<div class="output">
Foods Name starts with C: kotlin.sequences.FilteringSequence@2f2c9b19
</div>
<br>
When we will access each items the filter will be applied

```kotlin
for (food in lazyFoodsStartWithC) {
    println(food)
}
```
<div class="output">
Cocacola
Chatpati
Cabagae
Ceral
Chicken
Corn
</div>
<br>

**Lazy Map:**

```
var lazyFoodMapped = foods.asSequence().map {
    println("Item $it accessed")
    it
}
println(lazyFoodMapped)
```
<div class="output">
kotlin.sequences.TransformingSequence@2f2c9b19
</div>

<br>
Accessing the first item:

```
println(lazyFoodMapped.first())
```
<div class="output">
Item Cocacola accessed
Cocacola
</div>

<br>
When we access the last item it have to access the previous items sequentially to reach the last item:
```kotlin
println(lazyFoodMapped.last()) 
```
<div class="output">
Item Cocacola accessed
Item Chatpati accessed
Item Orange accessed
Item Lemon accessed
Item Cabagae accessed
Item Ceral accessed
Item Chicken accessed
Item Potato accessed
Item Corn accessed
Corn
</div>

<div class="warning">A lazy map or filter function can execute from the start to where it is called again again no matter how many times its item get accessed</div>



<br><br><br>

## Class
Check this examples
```kotlin
class Person {
    var firstName: String = ""
    var lastName: String = ""
    var birtyYear: Int = 0
}

val person = Person()
person.firstName = "Prince Billy Graham"
person.lastName = "Karmoker"
person.age = 1999
```

**Shorter Version:** Passing values in constructor and initializing properties in body
```Kotlin
class Person(fn: String, ln: String, btyr: Int) {
	var firstName: String = fn
	var lastName: String = ln
	var birtyYear: Int = btyr
}
val person = Person("Prince Billy Graham", "Karmoker", 1999)
```

**Shortest Version:** Passing values,  declaring & initializing properties in default constructor

```kotlin
class Person(val firstName: String, val lastName: String, val birthYear: Int)
val person = Person("Prince Billy Graham", "Karmoker", 1999)
```

### Init block
We can define as many init block as we want inside the class. All the init blocks will execute when an instance is created. You can assume it as constructor body in c++ or `__init__` in python

```kotlin
class Person(val firstName: String, val lastName: String, val birthYear: Int) {
    init {
        println("New Person: $firstName $lastName")
    }
    init {
        println("age: ${2020 - birthYear}")
    }
}
val person = Person("Prince Billy Graham", "Karmoker", 1999)
```
<div class="output">
New Person: Prince Billy Graham Karmoker
age: 21
</div>
<br>

### Constructor Overloading / Secondary Constructor
<div class="warning">Avoid function overloading when same thing can be implemented by default argument</div>
* `var` and `val` as parameter is not allowed as argument
* The overload constructors have to call the primary constructor using `this` keyword
* The signature has to be different than other constructors

```kotlin
class Person(var firstName: String, var lastName: String, var birthYear: Int = 2020) {
    constructor(age: Int, fn:String, ln:String): this(fn, ln, 2020 - age) {
        println("Use second constructor")
    }
    init {
        println("\nNew Person: $firstName $lastName")
        println("age: ${2020 - birthYear}")
    }
}
val person = Person("Prince Billy Graham", "Karmoker", 1999)
val person2 = Person(23, "Steve Nicholas", "Gonsalves")
val person3 = Person("Liam", "Patrick")
```

<div class = "output">

New Person: Prince Billy Graham Karmoker
age: 21

New Person: Steve Nicholas Gonsalves
age: 23
Use second constructor

New Person: Liam Patrick
age: 0
</div>
<br>

### Setter and Getter
**Setter function rules**
* Only applicable to `var` variables
* The value is passed as argument


**Getter function rules** 
* Applicable to both `var` and `val` variables
* must return correct type of data

```kotlin
class Person(var firstName: String, var lastName: String, var birthYear: Int = 2020) {
    var age: Int
    	get() = "2020 - birthYear"
    	set(value) {
            year = 2020 - value
        }
   
    init {
        println("$firstName $lastName ($age)")
    }
}
```

### Property Visibility Modifier

`public`: visible to everywhere<br>
`internal`: visible through out the module (eg. library, application)<br>
`protected`: visible to its own class and sub-classes<br>
`private`: only visible to its own class

eg. We can make birthYear a private variable
```kotlin
class Person(var firstName: String, var lastName: String, private var birthYear: Int = 2020) {
    ...
}
```
### Static property / Companion Object
//TODO
### Extension function 
//TODO


<br><br><br>

### Inheritance 
We can inherit from the following types of classes
* **`open` class**: A Class that allows itself to be inherited / subclassed
* **`sealed` class**: A sealed class is a class that can be subclassed, but only inside the file in which it's declared. If you try to subclass the class in a different file, you get an error.
* **`abstract` class**: A class that is incomplete and cannot be instantiated. you can declare properties to be implemented later by using `abstract` keyword before the property
* **`interface`**: Not a class but a structure that enforce some properties to be implemented, this may provide some default implementation
//TODO
<br><br><br>

### Singleton Class / Single instance Class
A class that can be instantiated only once
* don't required `class` keyword
* cannot be defined inside local scope
* other rules are same as regular class

```kotlin
object Warning{
    val backGroundColor = "orange"
    val textColor = "red"
    val icon = "exclamation"
}
```
<div markdown="1" class="info">
Singleton class can be used for interface delegation

```kotlin
interface AlertBoxExtras {
     val backGroundColor: String
     val textColor: String
     val icon: String
}

object Warning: AlertBoxExtras {
    override val backGroundColor = "orange"
    override val textColor = "red"
    override val icon = "exclamation"
}

class WarningAlertBox: AlertBoxExtras by Warning {
    val padding:Int = 10
    val margin:Int = 10
    val borderRadius: Int = 10
    
    init {
        draw(this)
    }
}
```
</div>

<br><br><br>

## Enum Class 
* Cannot be defined in local scope
* use `name` property to get the name of item
* use `ordinal` property to get the index


**simplest version:**
```kotlin
enum class Color{ RED, GREEN, BLUE }
fun main() {
    println(Color.BLUE) //BLUE
    println(Color.BLUE.name) // BLUE
    println(Color.GREEN.ordinal) // 1
}
```

**Customizing value:**

```kotlin
enum class Color(val rgb: String, val hexInt: Int, val hex:String) {
        RED("rgb(256, 0, 0)" , 0xFF0000, "#F00"),
        GREEN("rgb(256, 0, 0)" ,0x00FF00, "#0F0"),
        BLUE("rgb(256, 0, 0)", 0x0000FF, "#0F0")
}
fun main() {
    println(Color.BLUE) // BLUE
    println(Color.BLUE.name) // BLUE
    println(Color.BLUE.rgb) //  rgb(256, 0, 0)
    println(Color.BLUE.hexInt) // 255
    println(Color.BLUE.hex) // #0f0
    println(Color.BLUE.ordinal) //2
}
```
<br><br><br>


## Generic
//TODO
### in type and out type //TODO