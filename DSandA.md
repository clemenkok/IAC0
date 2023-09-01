# Data Structures and Algorithms

**This page will detail key notes on Data Structures and Algorithms, the primary topic tested in coding aptitude tests for internships and full-time jobs alike. It will use Python syntax and psuedocode (although using C++ syntax as an alternative shouldn't be too difficult)**

## Contents
- [Data Structures and Algorithms](#data-structures-and-algorithms)
  - [Contents](#contents)
  - [Tuples](#tuples)
  - [Lists](#lists)


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

days_of_the_week = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"] # we use square brackets instead of round brackets, that is the only syntactical difference between a tuple and a list.



```














