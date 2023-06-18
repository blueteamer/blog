---
title: "My Python Cheat Sheet"
date: 2023-06-18T08:13:05+02:00
draft: false
---

This is a brief overview and some notes of my Python learning progress. 
I installed and use Python on a Windows 10 device, dedicated to my Python skill improvement. Feel free to follow along. 

## Installation of Python
```
winget install anaconda.anaconda3
```
 

## Integrated Development Environments (IDEs) 
PyChar Community Edition by Jetbrains 
Visual Studio Code with Python Extension by Microsoft (also nice for later Jupyter Notebooks) 

## Python 

### Variables and basic types 
```
name = input("What is your name? ")
age = int(input("What is your age? "))
height = float(input("How tall are your? (in cm) "))
home_location = input("Where are you from? ")
current_year = int(input("What year is it? "))

year_of_birth = current_year - age

print("It seems your name is " + name + ", you are " + str(age) + " years old, " + str(height) + " cm tall. ")
print("You are from " + home_location + " and you were born in " + str(year_of_birth) + ". ")
print("Are these information correct?")
```


### Type casting 
```
a_number = 4
a_floating_number = 3.14 
a_string = "Wow. Awesome. Splendid." 
a_number_as_string = "12"
a_floating_number_as_string = "43.4322"

sum_of_numbers = a_number + int(a_number_as_string)
sum_of_floating_numbers = a_floating_number + float(a_floating_number_as_string) 

print("The sum of the numbers is " + str(sum_of_numbers))
print("The sum of the floating numbers is " + str(sum_of_floating_numbers))
```


### For loop 
```
for i in range(0, 10):
    print("This for-loop will be executed for a definite amount of times. In this case the " + str(i) + ". time. ")

print("Program finished. ")
```


### While loop 
```
keep_running = True
while keep_running:
    print("A while loop is an indefinite loop. It runs until a break condition will appear. ")
    print("In this case, the loop will run until 'keep_running' will be set to 'False'. ")
    keep_running = eval(input("Do you wish to continue? (Type 'True' for yes, 'False' for no): "))

print("Program finished.")
```


### Conditions a.k.a. if-statements 
Simple if-statement 
```
name = input("What is your name? ")
age = int(input("What is your age? "))

if age >= 40:
    print("You're old af. ")
else:
    print("You're whole life lies upon you. ")

print("Program finished. ")
```

Complex if-statement
```
name = input("What is your name? ")
age = int(input("How old are you? "))

if age < 5:
    print("You are probably in Kindergarten. ")
elif age >= 5 and age <= 18:
    print("You're probably in school. ")
elif age > 40 or name[0] == 'A':
    print("You're old OR your name starts with an capital 'A'. ")
else:
    print("Non of the defined conditions were matched. ")

print("Beware that the order of the conditions matter!")
print("Program finished. ")
```

Invert boolean value with not() 
```
age = int(input("How old are you? "))

if not(age < 18):
    print("You might be an adult.")

print("Program finished.")
```


### Array 
A string is an array of characters. 

```
a_string = "Something is going on!"

from_start_to_fourth = a_string[:4]
from_fourth_to_end = a_string[4:]
from_fourth_to_eight = a_string[4:8]
from_fourth_to_eight_but_only_every_second = a_string[2:12:2]
revert_the_string = a_string[::-1]

print("Get first 4 characters from start on : " + from_start_to_fourth)
print("Get substring from index 4 until the end of the string: " + from_fourth_to_end)
print("Get substring from index 4 to 8: " + from_fourth_to_eight)
print("Get substring from index 2 to 12, but only every second character: " + from_fourth_to_eight_but_only_every_second)
print("Revert the string: " + revert_the_string)
```

### List 
```
a_list = ["Something", "is", "going", "on", "here"]

print("This is what it looks like to print a list: ")
print(a_list)

print("This is how to iterate through a list and the result looks like this: ")
for item in a_list:
    print(item, end=" ")
print()

```

Some useful functions 
```
print("get the element of a specific index")
first_item = a_list[0]
print(first_item)

print("change the value of an element at a specific index")
a_list[0] = "What"
for item in a_list:
    print(item, end=" ")
print()

print("add element")
a_list.append("!")
for item in a_list:
    print(item, end=" ")
print()

print("remove the last element")
a_list.pop()
for item in a_list:
    print(item, end=" ")
print()

print("remove a specific element")
a_list.remove("here")
for item in a_list:
    print(item, end=" ")
print()

print("add element at a specific index in the list")
a_list.insert(0, "Wow")
for item in a_list:
    print(item, end=" ")
print()

print("sort the list")
a_list.sort()
for item in a_list:
    print(item, end=" ")
print()

print("clear the list")
a_list.clear()
for item in a_list:
    print(item, end=" ")
print()
```

### Tuple 
A tuple is a collection which is unordered and unchangeable. It is used to stack information which belongs together. 

```
employee = ("Hans Gruber", 38, "Assassin")

print(employee)

print(employee.count("Hans Gruber"))
print(employee.index("Assassin"))

for entry in employee:
    print(entry)

if "Assassin" in employee:
    print("There is an assassin.")

```

### Set 
A set is a collection which is unordered and unindexed. It will not hold duplicate values. A set is quite useful for comparing multiple values. 

```
cars_A = {"Audi", "BMW", "Mercedes", "VW", "Mercedes"}
cars_B = {"Audi", "BMW", "Skoda", "Ford", "Ferrari", "Fiat", "Citroen", "Peugeot"}

for car in cars_A:
    print(car)

cars_A.remove("Audi")
cars_A.add("Audi") 
cars_A.clear() 

# combine sets 
cars_A.update(cars_B)

all_cars = cars_A.union(cars_B)

# find differences 
cars_A.difference(cars_B)
cars_B.difference(cars_A)

# find commons 
cars_A.intersection(cars_B)
```

### Dictionary 
Similar to other languages a Dictionary is a changeable, unordered collection of unique key/value pairs. Dicts are pretty fast in processing as they use hashing to access values. 

```
employees = {"00001": "Horst Bader",
             "00002": "Fran Morgan",
             "00022": "Greg Mann"}

fran = employees["00002"]
# Error prone as a missing index will lead to an exception 
# Better use .get() function 

unknown_user = employees["asdf"]
# -> exception 

unknown_user = employees.get("asdf")
print(unknown_user) # -> None 

employees.keys()

employees.values()

employees.items()

for k, v in employees.items():
    print("The key: " + k)
    print("The value: " + v)
    
employees.update({"00023":"Another User"}) 

employees.pop("00022") # -> remove Greg Mann from the dictionary 
employees.clear() # -> clear the dictionary 
```


### Functions 
```
def print_welcome_statement(name, year, reason):
    print("Dear " + name + ", ")
    print("welcome to the " + reason + " which is taking place in " + str(year) + ". ")

def print_goodby_statement(name):
    print("Good by " + name + "! ")

print_welcome_statement("John Doe", 2023, "Ant counting championship")
print_goodby_statement("John Doe")
```

In case you are not aware of the amount of arguments to process (*args): 
```
def sum_up_some_numbers(*args):
    result = 0
    for number in args:
        result = result + number

    return result

r = sum_up_some_numbers(1, 2, 3, 4, 5 ,6 ,7 ,8 ,9 ,19)
print(r)
```

This can even be done by providing a dictionary of arguments (keyword args or **kwargs): 
```
def concatenate_several_strings_in_one_line(**somewords):
    print("Good day! ", end="")
    for key, value in somewords.items():
        print(value, end=" ")
    print("Bye!")


concatenate_several_strings_in_one_line(first="What", second="Is", third="Going", fourth="On")
```

### Modules 
Modules are separate *.py files which can be used to separate functionality in different Python files (separation of concerns). 

For instance, create a file/module for helper functions. 
<image of a separate file>

The structure looks like this: 
root
|-- main.py 
|-- custom_helper.py 

Content of "custom_helper.py"
```
def print_welcome_statement(name, year, reason):
    print("Dear " + name + ", ")
    print("welcome to the " + reason + " which is taking place in " + str(year) + ". ")

def print_goodby_statement(name):
    print("Good by " + name + "! ")
```

Now we have different ways to include that code in our main script file: 
```
import custom_helper

custom_helper.print_welcome_statement("John Doe", 2023, "Steven Seagull Lookalike Championship")
custom_helper.print_goodby_statement("John Doe")
```

With an alias 
```
import custom_helper as helper

helper.print_welcome_statement("John Doe", 2023, "Steven Seagull Lookalike Championship")
helper.print_goodby_statement("John Doe")
```

Include selected functions or classes 
```
from custom_helper import print_welcome_statement, print_goodby_statement

print_welcome_statement("John Doe", 2023, "Steven Seagull Lookalike Championship")
print_goodby_statement("John Doe")
```

With the 'from' statement you can also use '*' to include all functions within the module. 
Also, if the module contains classes, you can also import these classes. 


### Next 
In the next part we will take a look at classes and inheritance. Also, error handling will be a topic. 



