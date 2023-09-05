# Data Structures and Algorithms

**This page will detail key notes on Data Structures and Algorithms, the primary topic tested in coding aptitude tests for internships and full-time jobs alike. It will use Python syntax and psuedocode (although using C++ syntax as an alternative shouldn't be too difficult). Some extra resources I would recommend to learn this are the Neetcode 150 (making sure to actually understand the algorithms, that should be the focus, not getting the syntax correct) and the Harvard CS50P (especially if you want to solidify your OOP knowledge). In addition to this, I found "Algorithms to Live By: The Computer Science of Human Decisions" by Brian Christian Griffiths useful, as it was much more concerned with data structures and algorithms' real life impacts and applications, rather than being completely focused on programming itself, meaning it was more digestible.**



## Contents
- [Data Structures and Algorithms](#data-structures-and-algorithms)
  - [Contents](#contents)
  - [Data Structures](#data-structures)
    - [Tuples](#tuples)
    - [Lists](#lists)
    - [Dictionaries (aka Hashmaps)](#dictionaries-aka-hashmaps)
    - [Sets (aka Hashsets)](#sets-aka-hashsets)
    - [Stacks](#stacks)
    - [Queues](#queues)
  - [Algorithms](#algorithms)
    - [](#)

## Data Structures

### Tuples

Tuples are immutable lists. They are defined using round brackets `()` and are indexed using square brackets `[]`. They are immutable, meaning that they cannot be changed once they are created. They are useful for storing data that will not change, such as the days of the week or the months of the year.

```
# Creating a tuple

days_of_the_week = ("Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday")

# Modifying a tuple

days_of_the_week[0] = "Mon" # this is not something that will work on a tuple, as they are immutable

# Accessing a tuple

print(days_of_the_week[0]) # prints "Monday"
```

### Lists

Lists, otherwise known as arrays, are mutable data structures that can be used to store data. They are defined using square brackets `[]` and are indexed using square brackets `[]`. They are mutable, meaning that they can be changed once they are created.

```
# Creating a list

days_of_the_week = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"] 

# We use square brackets instead of round brackets, 
that is the only syntactical difference between a tuple and a list. #

# Modifying a list

days_of_the_week[0] = "Mon" # this is something that will work on a list, as they are mutable

# Accessing a list

print(days_of_the_week[0]) # prints "Monday"
```

### Dictionaries (aka Hashmaps)

Dictionaries are just the terminology used in Python to refer to maps in other languages. They are defined using curly brackets `{}` and are indexed using square brackets `[]`. They are mutable, meaning that they can be changed once they are created. Dictionaries contain a key and a value, and are useful for storing data that is not ordered, such as a list of students and their grades. We can access the objects (key and value) in the dictionary, searching with the key, value or both!

```
# Creating a dictionary

student_grades = {"John": 80, "Jack": 90, "Jill": 100}

# Modifying a dictionary

student_grades["John"] = 85 # this is something that will work on a dictionary, as they are mutable, John's grade got moderated up

# Accessing a dictionary

print(student_grades["John"]) # prints "80"

# Accessing the values of a dictionary

print(student_grades.values()) # prints "dict_values([80, 90, 100])"

``` 
In essence, a dictionary is just a special variety of a set, where each element in the set is a tuple of two elements, the key and the value. This will become clearer once you learn about sets.


### Sets (aka Hashsets)

Sets are data structures similar to lists, but they are unordered, and cannot contain duplicates, rendering them useful for common interview questions such as Valid Anagram or Contains Duplicate. They are defined using curly brackets `{}` and are indexed using square brackets `[]`, the same as dictionaries, the interpreter deciphers whether what you are defining is a set or dictionary based on what is inside the curly braces. They are mutable, meaning that they can be changed once they are created. 

```
# Creating a set

days_of_the_week = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"}

# Modifying a set

days_of_the_week[0] = "Mon" # this is something that will work on a set, as they are mutable

# Accessing a set

print(days_of_the_week[0]) # prints "Monday"

```

### Stacks

Stacks are "first in, last out" data structures, meaning that the first element to be added to the stack is the last element to be removed from the stack. They are useful for storing data that needs to be accessed in reverse order, such as a list of webpages visited, or a list of commands entered. They are defined using the `stack` class, and are indexed using square brackets `[]`. They are mutable, meaning that they can be changed once they are created. You should have encountered them in first year DECA.

```
# Creating a stack

stack = []

# Adding to a stack

stack.append("Monday")

# Removing from a stack

stack.pop() # removes the last element from the stack, in this case "Monday"

# Accessing a stack

print(stack[0]) # prints "Monday"

```

### Queues

Queues are "first in, first out" data structures, much like their real-life counterparts. They are useful for storing data that needs to be accessed in the order it was added, such as a list of people waiting in line. They are defined using the `queue` class, and are indexed using square brackets `[]`. They are mutable, meaning that they can be changed once they are created.

```
# Creating a queue

queue = []

# Adding to a queue

queue.append("Monday")

# Removing from a queue

queue.pop(0) # removes the first element from the queue, in this case "Monday"

# Accessing a queue

print(queue[0]) # prints "Monday"

```

As we can see from the syntax, in Python, stacks and queues are just lists with some extra functionality. This is because Python is a high-level language, and the developers of Python have already implemented these data structures for us. In lower-level languages such as C++, we would have to implement these data structures ourselves, which is why it is important to understand how they work.

## Algorithms

###  

















