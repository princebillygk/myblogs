---
layout: collection_item
title:  "Python Programming Notes"
category: Python
tags: python
---
# Hello world
```python
print("Hello world")
print("Second line")
```
Notice that these two line are printed in different lines by default becuase print function automatically adds a newline character after it has done printing the first parmeter. Now what if we want to end with a diffrent character like " " (space) ? 
```python
print("Hello world", end=" ")
prinnt("Second line")
```
Notice that both print functions is displaying its output in the sameline

# One thing that you should always remind while choosing python
* Python is a interpreted language so it good for writting short scripts, testing, problem solving
* Python is not suitable for big software and insfrastructure because there will be more chance to error.

# if-elif-else
Why this first? python supports some advance types of conditional expression lets see
```python
 if 18.5 <= weight / height**2 < 25:
    print("BMI is considered 'normal'")
```
Did you see it? We didin't need to include `and` here like any other programming languages. 

Some other regular expression: 

```python
if is_raining and is_sunny:
    print("Is there a rainbow?")

if (not unsubscribed) and (location == "USA" or location == "CAN"):
    print("send email")
```

Also please notice that it is `elif` instead of `else if` like any other programming language

# Mathemetical Operators:
```python
a + b # Adds two numbers
a - b # Subtracts b from a 
a * b # Mutliplies a and b  
a / b # Divides  a by b
a**b # Elevates a to the power of b
a // b # Integer part of the integer division of a by b
a % b # The remainder part of the integer division of a by b
```

# Logical Operators
* `and` requires both expression to be true
* `or` requires atleast one expression to be true
* `not` inverts the result of a expression


## Variable Types

**integer:** Stores integer values

**float:** Stores float values

**boolean:** Boolean values either `True` or `False`

**string:** Stores strings

### Strings 
Strings in python is immutable. We cannot modify a single index of a string. Instead we have to assign a new string.
We can read a single index of a string by using string index
```python
str = "Prince Billy Graham Karmoker"
print(str[4]) # prints "c"
```
We can also know the index of first occurence of a substring in a string
```python
str = "Prince Billy Graham Karmoker"
str.index("Graham") # prints "13"
```
We can also use `in` keyword to find if a substring exist in another string
```python
"Billy" in "Prince Billy Graham Karmoker" # return true
"Winy" in "Prince Billy Graham Karmoker" # return false
<<<<<<< HEAD
```
=======
>>>>>>> f9ee4aece27ab09776b16438239f58d9a6139f66


### Variable naming rules

1) Underscore (\_), numbers and letters are allowed in a variable name
2) A variable must start with either underscore (\_) or a letter
3) Python is case sensitive



## Know the type of a variable
To know the type of a specific function we can use the `type(variable)` function 
```python
print(type(2)) # Prints "int"
print(type("a")) # Prints "string"
print(type(3.5)) # Prints "float"
```



## Global Variable

if we want to read a global variable inside a function its OK

```python
x = "awesome"
def myfunc():
  print("Python is " + x)
myfunc() # awesome
```

but if we try to modify a global variable inside a function we need to us global keyword 

```python
x = "awesome"
def myfunc():
  global x
  x = "hello world"
  
myfunc()
print("Python is " + x) # hello world
```



## Casting data types

```python
intVariable = 3;
print("She is  " + str(int));
```



## String

Strings are immutable in python. we cannot change string character by index

### Multiplication of string in python: 

expression `"hello " * 3` will return "hello hello hello "

### Concatenation of string:

```python
firstName = "Prince";
lastName = "Billy"
fullName = firstname + ' ' + lastname # "Prince Billy"
```

### Index in string

We can access characters of string using index

``` python
python = "Python"
python = python[0] #returns 'P'
```

negative index will start counting from last. index -1 will return the last element

```python
python[-1] # returns 'n'
```

### String slicing

**syntax**:

```python
str[start:end] # items start through end-1
str[start:]    # items start through the rest of the array
str[:end]      # items from the beginning through end-1
str[:] 		 #returns full string
```

### Check weather a string contain in another string

```python
"billy" in "prince in billy graham karmoker" #returns true
"meow" in "prince in billy" #returns false
```

### Define multiline string

We can define multiline string using three """ double quotation mark. can be used to write doc.

other name doc-string

```python
"""
This is 
a multi-lin
string """
```

### Get string length

```python
len(str)
```

### String Formatting

```python
"This is a string %s." % "prince"
"This is a number %d." % 34
"My name is %s I am %d" % ("Prince", 22)
```



## List

### List can be indexed and sliced like string

```python
myvar = [34, 2, 3, 53, 15];
myvar[0] #34
myvar[-2] #53
myvar[2:] #[3, 53, 15]

//clearing a range of list using slice
myvar[2:4] = []
```

### Append to list

```python
myvar.append(34) #appends an item to list
```

### Copying a list:

```diff
my_foods = ['Potato mash', 'Pizza', 'Bakon', 'Banana']
- friend_foods = my_foods #makes a alias to to my_foods
+ friend_foods = my_foods[:] #use slice operator to make a real copy
```

### List Comprehension

```python
cubes = [i ** 3 for i in range(1, 11)]
evens = [i for i in range(1, 11) if i % 2 == 0]
odd_enen = [(i, "even") if i % 2 == 0 else (i, "odd") for i in range(1, 11) ]
```



## Tuple

Same as list but we cannot add, change or delete in tuples. 

```python
binarydigits = (0, 1);
```

A tuples with single item must have trailing (,) comma:

```python
oneValue = ("me",)
```



## Dictionary

Similar to list but we access it using key rather than index

The following types are allowed to be used as dictonary keys:
* Number
* String
* Boolean
* Tuples

```python
dct = {'key1' : "value1", 'key2' : "value2"}
```

Return all keys & values dictionary:

```python
dct.keys(); #return keys
dct.values(); #return values	
```

```python
for key in dct:
	print(key)

for key in dct.keys():
	print(key)

for value in dct.values():
	print(value)

for key, value in dct.items():
	print(key, value)
```
```
dct.update(other_dct) # Update a dictonary using other dictonary, updates existing keys and add new keys from other dct
dct.clear() # Removes all the items of the dictonary 
```




### In Keyword with List, Tuple and Values

Check weather a value is in list or tuple

```python
values = [43, 5, 2]
43 in values #True
tup = (34,3,2);
35 in tup #False
```

Check weather a key exists in tuples

```python
person = {
	'firstname' : 'Prince Billy Graham', 
	'lastname' : 'Karmoker'
	'age' : 22
}
'lastname' in person #True
```



### Array/ Tuple Destructing:

```
foo, boo, *aoo= ['FOO', 'BOO', 'MOO', 'GOO', 'LOO']
print(foo)
print(boo)
print(aoo)
```

**Output**:

```python
FOO
BOO
['MOO', 'GOO', 'LOO']
```



### IS and NOT Operator

```python
name = 'John'
name is 'John'
name is not 'Tom'
```



## Function

#### Keyword argument:

We can explicitly specify the argument in any order without remembering their position

```python
def describe_pet(animal_type, pet_name):
    """Display information about pet"""
    print("I have a " + animal_type +  ".");
    print("My " + animal_type + "'s name is " + pet_name.title() + ".");

describe_pet("bird", "Cute Pie");

#explicitly specifing the argement in any order
describe_pet(pet_name = "Meo", animal_type="Cat")
```

#### Arbitrary number of argument

```python
def make_pizza(size, *topings):
    "This function allows arbitrary number of arguments"
    print ("Creating a pizza of size " + str(size))
    if topings:
        for item in topings:
            print("- " + item);
    
make_pizza(12, 'cheese', 'sause', 'meoneese');
make_pizza(5)
```

#### Arbitrary number of keyword argument

```python
def build_profile (first, last, **user_info):
    profile = {
            'firstname' : first,
            'lastname' : last
            }

    for k, v in user_info.items():
        profile[k] = v

    return profile;

user_profile = build_profile("prince billy graham", "karmoker")
user_profile = build_profile("winy", "chicham", age=17, gender= "female", hobbies=['art', 'game'])
print (user_profile)

```

**When we include both kind of Arbitrary arguments we have to keep the non keyword argument first**.

Example

```python
def myfunc(positional_arg1, positional_arg2, *arb, **key_arb):
    ...
```

### Lambda function

```python
lambda: "hello world" # a function that returns hello world
lambda x, y: x * y # a function that takes argument x, y and return x * y
```



## Import

```python
import package_or_module_name
import package_or_module name as x

from package_or_module import yfunction
from package_or_module import yfunction as x

from package_or_module import pfunction, qfunction, sfunction as x, zfunction
```



## Class

#### `self`

`self` is the first parameter of python class. self is the first parameter of class method. used to access its own method and properties

#### `__init__()` 

Constructor

#### `__str__()`
Return the string representaion of the class here

#### Class Inheritance

```python
class Car():
    """A simple attempt to represnt a car"""

    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def get_descriptive_name(self):
        """prints year, make and model"""
        long_name = str(self.year) + ' ' + self.make + ' ' + self.model
        return long_name.title()

    def read_odometer(self):
        """prints odometer reading"""
        print("This car has " + str(self.odometer_reading) + " miles on it.")

    def update_odometer(self, mileage):
        """update odometers based on conditions"""
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back an odometer")
            
    def increment_odometer(self, miles):
        self.odometer_reading += miles

class ElectricCar(Car): 
    """Represents aspects of a car, specific to electric varhicles"""

    def __init__(self, make, model, year):
        super().__init__(make, model, year)

    def print_descriptive_name(self):
        #print(super().get_descriptive_name()); #this will work but
                                                #no need to call super everytime
        print(self.get_descriptive_name());     #we can use self to access super
                                                #class members

car = Car("Bangladesh", "Walton", 2024)
print(car.get_descriptive_name())
car.read_odometer()
mytesla = ElectricCar("USA", "Tesla 403x", 2024)
print(mytesla.get_descriptive_name())
mytesla.print_descriptive_name()
```



#### Try-except

```python
try:
    number1 = input("Input a number: ")
    number2 = input("Input another number: ")
    result = number1 / number2
    with open("test.txt", "r+") as test:
        contents = test.read().rstrip()
        test.write(str(result))
except ZeroDivisionError:
    print("Division by 0 is not allowed")
except IOError: 
    print("File not found")
else:
   print( contents)  #do something if no error occured
```

## Ternary condition

```python
age = 23
stmt = "You can watch this movie" if age > 18 else "You cannot watch this movie"
```

## IS

```python
# check it a object refers to same object and the value is also same 
age = 1
if age is 1: # same as if (age === 1)
```



## Some important functions and different uses:

### string

```python
#case
str.upper() #converts string to uppercase
str.title() #capitalizes only first letter and makes lower case all other letters
str.lower() #converts string to lowercase
str.count("e") # Count the number of occurance of a certain substring
str.index("r") # Get the index of first occurance of a substring
str.endswith("r") # Check if a string ends with certain substring

#strip
str.strip() #removes whitespaces arround the string
str.lstrip() #removes whitespaces only from left sides
str.rstrip() #removes whitespaces only from right side

#checker
str.isdigit() # check if str is digit "4545.34" -> False "3432" -> True "err324" -> False
str.isalpha() # checks if a string contains only letters
str.isnumeric() # Checks is a number is numeric

## String Formating
```python
print("Hello {}, your luck number is {}".format(name, number)
print("Hello {name}, your luck number is {number}".format(name=name, number=number)) 
```
### Format spcifier
```python
print("This is two decimal point number {:.2f}.format(34,34343))
```



Expr | Meaning | Example 
--- | --- | --- 
{:d} | integer value | '{:d}'.format(10.5) → '10' 
{:.2f} | floating point with that many decimals | '{:.2f}'.format(0.5) → '0.50' 
{:.2s} | string with that many characters | '{:.2s}'.format('Python') → 'Py' 
{:<6s} | string aligned to the left that many spaces | '{:<6s}'.format('Py') → 'Py    ' 
{:>6s} | string aligned to the right that many spaces | '{:>6s}'.format('Py') → '    Py' 
{:^6s} | string centered in that many spaces | '{:^6s}'.format('Py') → '  Py ' 

# join array of string
"seperator".join(["hello", "world"]) # "Helloseperatorworld"

# split a string
"This is  me".split() # returns ["This", "is", "me"]
```

### list

```python
## add item
ls.append(item); #adds an item to the end of list 
ls.insert(0, item); #inserts an item at any position of the string


## remove an item 
del ls[2] #removes the item at index 2
last_item = ls.pop() #removes and returns the last item from list
ls.pop(2) # removes the item at index 2
last_item.remove('value') #remove an item using its value
ls.clear() # Clears all the item of a list
ls.copy() # Cretaes a copy of the list
ls.extend(other_list) # appends all element of other list


## sorting
# permenent sorting
ls.sort() #permenent sort in ascending order
ls.sort(reverse = True) #permenent sort in ddscending order
#temporary sort
sorted_ls = sorted(carsp)
sorted_ls = sorted(cars, reverse = true)

## looping throw a list 
for magician in magicians:
    print (magician) #prints all magician in magicians
## loop with index value
for index, magician in enumarate(magicians):
    print (magician)#prints all magician in magicians
    print(index) #prints the index

    
## statistical functions
min(ls) #prints the minmum in a list of same catagory items
max(ls) #prints the maximum in a list of same catagory items
sum(ls) #prints the sum from a number list


## list comprehension using range
cubes = []
for i in range(1, 11):
    cubes.append(i ** 3)

    
## filter function
a = [1,4, 5]
b = [1,5]
c = list(filter(lambda x: x not in b, a)) # [4]

## reduce function
nubmers = [2, 34, 5, 33, 2, 2]
product_of_all_numbers = reduce(lambda x, y: x * y, numbers)
```



### Range

```python
a_range_of_4_items = range(4) #returns a range of 4 items
myrange = range(i, j) #contains i to j-1 element
myrange = range(2, 100, 2) #contains all even number range(start, end-1, step)
```



# Working with files

#### Reading a file

```python
with open("test.txt") as text_file:
    contents = text_file.read()
    print(contents.rstrip()) #rstrip removes the extra blank line caused by eof
```

##### Reading a file line by line

```python
with open("test.txt") as text_file:
	for line in text_file:
		print(line.rstrip()) #restrip removes the extra blank line cause by \n at the end of each line
```

##### Read all lines and store each line as item in list

```python
with open("test.py", "r") as text_file:
	lines = text_file.readlines();
```

#### Writing lines

```python
with open("test.txt", "w") as text_file:
    text_file.write("I love programing\n")
    text_file.write("I love python so much\n")
    text_file.write("My favourite programing language is typescript\n")

```

#### File opening modes

```python
"r" #read mode
"w" #write mode
"a" #append mode
"r+" #read and append mode 
```



## Mathematical Functions

```python
list1 = [1, 2, 3]
math.prod(list1) # return 1 * 2 * 3fr
```

