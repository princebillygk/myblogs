---
layout: post
author: Prince Billy Graham Karmoker
title:  "Kotlin Learning"
date:   2020-09-25 16:14:26 -0500
categories: kotlin
---

# How you should learn kotlin?
* **[Take Kotlin Koan Course](https://kotlinlang.org/docs/tutorials/koans.html)**: I don't prefer edutool for this, it is slow and sluggish. the online playground is better
* If you are a python programmer you must make use of **[Khan Academy kotlin course (text based)](https://khan.github.io/kotlin-for-python-developers/)** - I really get helped from it.
* **[Go through the codelab courses](https://developer.android.com/courses/basic-android-kotlin-training/overview)** - you can skip the android specific courses for now.
* Here's the official website **[documentation](https://kotlinlang.org/docs/reference/)** - at least go through once.
* And last but not least revision this blog every time you start your new project

if you are into competitive programming you can also read this **[article](https://kotlinlang.org/docs/tutorials/competitive-programming.html)** from official website.

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
colors.joinToString() // returns "Red, Green, Blue" 
colors.joinToString("+") // returns "Red+Green+Blue"
```






