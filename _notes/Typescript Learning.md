---
layout: collection_item
title:  "Typescript Notes"
category: Typescript
tags: typescript, javascript
---
# Typescript Notes

## Types:

* ### `number`:
  All numbers in javascript are either floatingpoint or biginteger in javascript So in typescript.
  #### `number` Literals:
  *decimal*: 10<br>
  *binary*:  0b10101011<br>
  *octal*: 0o2341<br>
  *hex*: 0x234ab<br>
  *bigint*: 1000n<br>
  example:
  ```typescript
  let marks: number = 23.353
  ```
  <blockquote>
    <b>Notes:</b> As all numbers in javascript is either number or integer so their is no separate type like <i>double</i> or <i>int</i>
  </blockquote>

* ### `boolean`:
  #### `boolean` Literals: true & false

* ### `string`:
  String Literal can be quoted with `""` double qoute or `''` single qoute.
  #### Template String:
  template strings are qouted with ``  ` `   `` backtick. We can insert expression inside a string template
  using `${expression}`:
  <br>example:
  ```typescript
   let name = "Prince Billy Graham Karmoker";
   let birthYear = 1999;
  
   let s1: string = `I am ${name}.`
   let s2 : string = `Hi my age is ${2021 - birthYear}`
  ```

* ### `Array` / `[]`:
  We can declare an array type in two ways.
  ```typescript
   let list: number[] = [1, 3, 5]
   let list2: Array<number> = [1,3, 5]
  ```

* ### Tuple:
  Tuples are kind of array with fixed number of elements where all the types are known.
  <br>example:
  ```typescript
  let x:[string, number]
  x = ["Prince Billy Graham Karmoker", 23 ]
  ```

* ### `enum`:
  ```typescript
  enum Subjects {
    Math, 
    English,
    Bengali
  }
  enum Brands {
    Lenvo = 3,
    Hp, 
    Tosiba
  }
  enum Color {
    Red = 1,
    Green = 2, 
    Blue = 4
  }
  ```
  We can get enum indexes using `.` operator:
  ```typescript
  let c:Color = Color.Green
  ```
  We can also get the enum item name using index:
  ```typescript
  let subjectName: Subject = Subjec[1]
  ```

* ### `unknown`:
  We can use this type when we don't know the type or aware other developer that the type can vary of this variable. **
  We need to do proper type checking before doing any type specific job with it.** The compiler will throw an error if
  we try to do any type specific work without checking the type of it.
  #### `unknown` Literals:
  Can be anything
* ### `any`:
  We can also use this when we don't know the type or when using a third party library which didn't declared the
  tyeps. **We don't need to any type checking before doing anything with it.**
  #### `any` Literals:
  Can be anything
* ### `void`:
  opposite of type `any`. **No type at all**. We can use this when declaring a function return type.
  <br>example:
  ```typescript
  function  warnUser(): void { //the return type is void
    console.log("This is my warning message.")
  }
  ```
  #### `void` Literals:
  `null`, `undefined`

  ### `never`:
  A value that never. for example a function that never returns.
  ```typescript
  function startServer(): never {
    server.port = 3000
    server.start()
  } 
  ```

### `object`:

Any non premitive type. Infact anything that is not `number`, `string`, `boolean`, `bigint`, `null`, `undefinded`
, `symbol`

### Type assertion:

type assertion means assuming something as other types. We can do it in two different way:

1) #### Using `as` keyword:
   ```typescript
   let strLength: number = (someValue as string).length
   ```
1) #### Using angle bracket:
   ```typescript
   let strLength: number = (<string>someValue).length
   ```

<br><br><br>

## Interface

```typescript
interface Person {
    name: string,
    age: number,
    hobbies?: string[]
}
```

optional properties in interface can be postfixed with `?`.

### Readonly Property:

```typescript
interface Point {
    readonly x: number;
    readonly y: number;
}
```

### Define function using interface

```typescript
interface SearchFunc {
    (source: string, subString: string): boolean
}
```

### Define Indexable type using interface

```typescript
interface specialArray {
    [index: number]: Animal;
}
```

### Define Class type using interface:

```typescript
interface ClockInterface {
    hour: number;
    minute: number;

    tick(): void;
}

interface ClockConstructor {
    new(hour: number, minute: number): ClockConstructor
}

function createClock(
    ctor: ClockConstructor,
    hour: number,
    minute: number
): ClockInterface {
    return new ctor(hour, minute)
}

class DigitalClock implements ClockInterface {
    constructor(h: number, m: number) {
    }

    tick() {
        console.log("beep beep");
    }
}
```

### Extending Interface 
We can also extend our interface from other interface or class,
But A interface that is extended from a class with private and protected property that interface can only be implemented by the subtype of the class.

## Function
Default parameter, optional paramenters are supported in typescript
### Writing the function type
```typescript
let myAdd: (x: number, y: number) => number = 
        function (x: number, y: number):number {
            return x + y;
        }
```
### Spread operator fo rest parameters:
We can also declare rest parameters using spread operators.

## Class
Class support set and get function. We can validate class using set function.
