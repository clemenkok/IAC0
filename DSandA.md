# Data Structures and Algorithms

**This page will detail key notes on Data Structures and Algorithms, the primary topic tested in coding aptitude tests for internships and full-time jobs alike. It will use Python syntax and psuedocode (although using C++ syntax as an alternative shouldn't be too difficult)**

## Contents
- [Data Structures and Algorithms](#data-structures-and-algorithms)
  - [Contents](#contents)
  - [Tuples](#tuples)
  - [Lists](#lists)
  - [Dictionaries](#dictionaries)


## Tuples

Tuples are immutable lists. They are defined using round brackets `()` and are indexed using square brackets `[]`. They are immutable, meaning that they cannot be changed once they are created. They are useful for storing data that will not change, such as the days of the week or the months of the year.

```
# Creating a tuple

days_of_the_week = ("Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday")

# Modifying a tuple

days_of_the_week[0] = "Mon" # this is not something that will work on a tuple, as they are immutable

# Accessing a tuple

print(days_of_the_week[0]) # prints "Monday"
```

## Lists

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

## Dictionaries

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














