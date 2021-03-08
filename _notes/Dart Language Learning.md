---
layout: collection_item
title:  "Dart Notes"
category: dart
tags: dart, flutter
---

# Dart language Learning

## Hello World
```dart
void main() {
  print('Hello World!');
}
```

### Comments
```dart
//this is a comment
```

## Variables:
Dart is a strongly typed language. If we don't specify the type it will be infered automatically from the intialization
```dart
var name = "Prince";
```
```dart
String name = "Prince";
```

If want a variable that can hold any type of values then we declare a dynamic variable in dart

```dart
dynamic name = "Prince";
name = 23;
```

An variable that is not initialized is null
```dart
int age;
print (age); //this prints "null"
```

## Final vs Const

final is a runtime constant that can be set only once whereas const have to be initialized at the time of declartion. final can be intialized later
```dart
const pi = 3.1416;

double calculateArea(final r) {
  return pi * r * r;
}

void main() {
  var radius = 23;
  print(calculateArea(radius));

}
```

	Notes: if we want to use const at class level we should be marked with static 	keyword

Example:
```dart
const key = "123acbd";
const double pi = 3.1416;
const baz = [];
```

We can also create constant value:
```dart
final me = const[];
```

## Builtin Datatypes
* ### `num`:
	includes basic operators (eg, + , / , *, -), bitwise operators and mathematical functions `abs()`, `ceil()`, `floor()`. There is two sub type of num:
	* #### `int` : 64bit
	* #### `double`: 64bit
<br>


* ### `String`:
  sequence of UFT-16 code units. you can use both the double qoute and the single qoute.
	example:
    ```dart
    var s = "I love my `Android Studio`"; // single qoute inside double oute
    var s1 = 'I love my "Android Studio"'; //double qoute inside single qoute
    var s2 = "I love my \"Android Studio\""; //delimiter
    ```
    ###### Concate string

   we can concate **adjacent string** using the plus operator
   ```dart
    print ("My name is Prince Billy Graham. " +
        "My age is 23" +
        "I am a student");
    ```

	###### Multiline String:
    We can also use tripple single qoute for multipline string:
    ```dart
    void main () {
  print ('''My name is Prince Billy Graham. 
        My age is 23
        I am a student''');
    }
    ```
    ###### Raw string: 
    In raw string special escape character doesn't work.
    ```dart
    print(r"My name is \n \? Prince Billy Graham.");
    ```
	###### String interpolation: 
    we can use `$` / `${}` (for complex expressin) to insert equation aor variable to string.
    ```dart
    void main () {
      var name = "Prince Billy Graham Karmoker";
      print('My name is "$name"');
      print('My name is "${name.toUpperCase()}"');
      print('My age is ${10+23}');
    }
    ```

* ### `boolean` : true / false
	 <br>
* ### `List`:
  looks like javascript array literals.
  ```dart
  var cars = [
	  'corola',
	  'honda',
	  if (person.class == "rich) 'BMW',
	  for (brand in bicycle) brand.name,
  ];
  ```
	To get the length of a list we can use `.length` property of a list.
	 ```dart
	 cars,length //3
	 ```
	 ### Maps
	 ```dart
	 void main() {
		  var cars = {
		    "bmw": "X34",
		    "tesla": "AX",
		    "corola": "100",
		  };
	  
		  print(cars["tesla"]); //AX
	}
	 ```
 
	 ### Enums
	 ```dart
	enum Color {
	  red, 
	  green, 
	  blue
	  }
	  
	void main() {
	 print(Color); //Color
	  print(Color.red); //Color.red
	  print(Color.values);  //[Color.red, Color.green, Color.blue]
	  print(Color.green.index); //1
	}
	 ```
	
## Control Statement
### if / if - else / if - else if / if - else if - else
Nothing so new about it, just how you are use it in C++/javascript/typescript/kotlin
 
## Functions
```dart
num addNumbers(int num1 , double num2) {
  return num1 + num2;
}

void main() {
  print(addNumbers(1,3.3));
}
```
A function with only one statement can also be written using fat arrow `=>` symbol. The statement will also return if the function needs to return something.
```dart
void main() => runApp(MaterialApp())
```

### Anonymous Function
#### single statement anonymous function:
```dart
() => "Hello World"     //<---- Also returns.
```
#### Multiple line anonymous function 
```dart
() {
print("Hello World")
return true
}
```

## Class 
```dart
class Person {
  String name = "Max"; 
  int age =30;
}


void main() {
  var p1 =  Person();
  print(p1.age)
}]
```
### Class with Constructor: 
```dart
class Person {
  String name;
  int age;
  
  Person(String inputName, int age) {
	  name = inputName; //automatically reqonizes that 'name' is a class property
	  this.age = age;
	  //specifying that 'age' is the property of class using this
  }
}

void main() {
  var person = Person("Prince Billy Graham", 543);
  print(person);
}
```
We can also use named argument here. Named arguments are optional by default. [**But while using flutter** we can also make a named argument required by adding `@required` before the argument].

```dart
class Person {
  String name;
  int age;
  
  Person({String name @required int age) { //currently @required anotion is only a flutter feature.
	  this.name = name;
	  this.age = age;
  }
}

void main() {
  var person = Person(name:"Prince Billy Graham", age: 543);
  print(person);
}
```
A more shorter way of coding the constructing will be using this keyword directly at the constructor argument and no body at all (optional) . example (change only on the constructor)
```dart
Person({this.name, this.age});
```
##### Constructor Overloading
We can also overload a constructore like this example:
```dart
```dart
class Person {
  String name;
  int age;
  
  Person({this.name, this.age}) {
	  this.name = name;
	  this.age = age;
  }
	
 //constructor overloading
 Person.veryOld(this.name) {
	 this.age = 80;
 }
}


void main() {
	Person("Prince Billy Graham Karmoker");
	Person.veryOld("Steve");
}
```
<br>

### Extending a class
We can also extend a class from a parent class using `extends` keyword. we can override parent class function inside subclass. **But when overriding a parent class function inside subclass we should use `@override` anotion which is not mandatory but good practice**
```dart 
class MyApp extends StatelessWidget {  
	@override
	Widget build (BuildContext context) { //overriding parent class
		return MaterialApp(home: Text("Hello World"));
	}
}
```

