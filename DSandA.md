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
    - [Heap](#heap)
  - [Algorithms](#algorithms)
    - [Sliding Window](#sliding-window)
    - [Binary Search](#binary-search)
    - [Depth and Breadth First Search](#depth-and-breadth-first-search)
    - [Dijkstra's Algorithm](#dijkstras-algorithm)

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

### Heap

Heaps are useful data structures to implement all sorts of algorithms. Heaps can be built in O(n) if all the values are known ahead of time.

## Algorithms

### Sliding Window

The sliding window algorithm uses two pointers to iterate through an array. A common problem that can be solved with this algorithm is the basic buy/sell stock problem, where the aim is to buy at it's lowest and sell at it's highest, assuming you are only permitted to make one transaction.

Following these criteria, we can tell that, in it's simplest terms, we want to take the point at which the difference between the left (buy) and right (sell) pointers are the highest. To do this, we can say that if the right pointer is lower than the left pointer, we just move the left pointer across, as there is no reason to buy when the stock is due to drop in value. 

However if the right pointer is higher than the left, we can store said value in a variable `max_profit`, provided the difference is greater than the existing value. At this point, we leave the left pointer where it is and move the right pointer incrementally to find the highest point, where we can sell.

```
  def maxProfit(self, prices: List[int]) -> int:
    l, r = 0, 1
    maxP = 0

    while r < len(prices):
      if prices[l] < prices[r]:
        profit = prices[r] - profit[l]
        maxP = max(maxP, profit) # no need for a comparison if statement
      else:
        l = r
      r += 1

    return maxP

```


### Binary Search

The binary search algorithm involves reducing the size of your set in half with every search. This is done by comparing the size of the value selected with the value you are searching for, then discarding the half of the set which is not relevant. The binary search is used for the valid perfect square problem.

**Given a positive integer num, write a function that returns True if the num is a perfect square, else False. Do not use built-in library fns such as sqrt.**

Set up two values left and right as 1 and `num`, and while left is less than right, we can calculate the midpoint. Now if the midpoint squared is less than num, we can set left to the midpoint, else if it is greater, we set right to the midpoint, and repeat. If the midpoint is neither greater nor less than, it is the num, and we can return True. We return false when we leave the while loop.

```
  def isPerfectSquare(self, num: int) -> bool:
    l, r = 1, num

    while l <= r:
      mid = (l + r) // 2 # the double slash is integer division
      if mid * mid < num:
        l = mid + 1
      elif mid * mid > num:
        r = mid - 1
      else:
        return True
    return False
```

### Divide and Conquer

Divide and conquer uses recursion (calling a function within the same function) to solve a question more effectively. There are three cases in every divide and conquer algorithm:

1. Base Case - the simplest possible case in which the problem can be solved
2. Recursive Case - the recursive steps to take, usually calling the function on two halves of the issues
3. Joining Case - what to do with the solutions presented by the recursive case.

Consider the **Largest subarray problem** - find the maximum sum of a subarray of an array (up to and including the entire array itself). We can break this question down into each of the three cases:

1. Base case: When the array has length 1, the maximum sum possible is just the value of the only element.
2. Recursive case: When the array has length > 1, split the array into two halves, and apply the function to each half. This has the effect of repeatedly doing this recursion on each half until we reach the base case.
3. Joining case: consider the two halves of an array:
[1, -3, 2, 4] and [2, -1, 3, -1]
From the recursive case, we find that the max possible subarray sum in each half is 6 and 3. However, on joining the two arrays, the maximum possible sum could be made from a subarray containing elements from both halves of the bigger array. To solve this, we can consider the maximum sum starting from the last element in the left array and going to the first element, and the maximum sum starting from the first element in the right array and going to the last element. Combining these sums gives us a "joining" maximum sum, which (in this case) is 10, made from the subarray [2, 4, 2, -1, 3].

We can then return the biggest of the three maximum sums, again (in this case 10). This method is $O(n*logn)$, whereas the brute force method of checking every possible subarray is $O(n^2)$.

**Why is this faster?**
The [Master Method](https://brilliant.org/wiki/master-theorem/) shows us that divide and conquer algorithms can be faster than their brute force counterparts. In this particular case, the master method is $T(n) = 2T(n/2) + O(n)$, which implies $T(n)=O(n*logn)$. This will be covered in more detail in the discrete mathematics course.

Implementation:
```
def arrsum(nums):
    sum = 0
    for i in nums:
        sum += i
    return sum

def maxSubArray(nums):
    if len(nums) == 0:
        return 0
    if len(nums) == 1:
        return nums[0]
    mid = len(nums) // 2
    left = nums[:mid]
    right = nums[mid:]
    leftSum = maxSubArray(left)
    rightSum = maxSubArray(right)
    
    joinSum = float('-inf')
    lsum = float('-inf')
    leftsum = 0
    for leftIndex in range(len(left)-1, -1, -1):
        leftsum += left[leftIndex]
        if leftsum > lsum:
            lsum = leftsum
    rsum = float('-inf')
    rightsum = 0
    for rightIndex in range(len(right)):
        rightsum += right[rightIndex]
        if rightsum > rsum:
            rsum = rightsum
    joinSum = lsum + rsum
    return max(max(leftSum, rightSum), joinSum)

```

### Dynamic Programming

Dynamic programming is a fancy way of saying that you are keeping track of previous results, as they will be used in future results. Consider the problem of printing up to the nth row of [Pascal's triangle](https://en.wikipedia.org/wiki/Pascal%27s_triangle):

n = 5
Output: 1 1 1 1 2 1 1 3 3 1 1 4 6 4 1 1 5 10 10 5 1

To print the rth item in the nth row, you can use a function called the choose function $\binom{n}{k}=\frac{n!}{(n-r)!r!}$. The simplest way to calculate the factorial is to use a loop, as below:
```
def factorial(n):
  if n==0:
    return 1
  sol = 1
  for i in range(2,n+1):
    sol *= i
  return sol
```
However, this becomes inefficient, as for all elements you will recalculate the factorial in n steps - when calculating 6!, you will recalculate 5! every single time. This makes the algorithm $O(n^3)$, as you need to print all $O(n^2)$ items, and calculating each item requires $O(n)$ steps.

To optimise this using dynamic programming, we can use a memo to keep track of what we have already calculated and reuse it, as a hashmap lookup is $O(1)$.

Implementation:
```
memo = {0:1}
def factorial(n):
  if n in memo:
    return memo[n]
  else:
    memo[n] = n*factorial(n-1)
    return memo[n]
    
def soln(n):
    for i in range(n+1):
        for r in range(i+1):
            print(int(factorial(i)/(factorial(i-r)*factorial(r))), end=" ")

```

Now, since the prior factorial values are stored in the memo, each call to factorial is $O(1)$ rather than $O(n)$. This reduces the algorithm from being $O(n^3)$ to $O(n^2)$.

### Depth and Breadth First Search

These are the two fundamental search algorithms that many other graph algorithms are built from, such as Djikstra's Algorithm, Prim's Algorithm etc, so they are vital to learn for use in trees and graphs. A common problem using the Depth First Search is Inverting a Binary Tree

**Invert a binary tree (Depth First Search)**

This involves recursion, as all the sub branches also need to be inverted. When the function is called on the root node, we recursively run the said function on the left and right subtree.

```
  def(invertTree(self, root: TreeNode) -> TreeNode)
    if not root:
      return None
    
    tmp = root.left
    root.left = root.right
    root.right = tmp # swapping branches

    self.invertTree(root.left) # recursive call on the left branch 
    self.invertTree(root.right) # " right branch
    return root
```

### Dijkstra's Algorithm

Dijkstra's algorithm is commonly used to solve graph problems where you need to find the shortest path, such as Network Delay Time, as explained below. This can be simplified to a Breadth First Search, using a minimum heap.

**You are given a network of n nodes, labeled from 1 to n. You are also given times, a list of travel times as directed edges times[i] = (u, v, w) where u is the source node, v is the target node, and w is the time taken for a signal to travel from source to target. We are sending a signal from a node k, return the time taken for all n nodes to receive the signal, else return -1.**

The time taken for all n nodes is the same as the maximum time taken for the furthest node to receive the signal. We use a breadth first search to find the shortest path, by adding the nodes we can visit to a frontier, which is a min heap in this case. We visit the node with the shorter path. The minimum heap has a path *key* and a node *value*. Once we add the two nodes connected to the initial node, we can pop off the initial node, as we have already visited it. We assign the **total** path count from the initial node in the heap, rather than just the previous path taken.

We can then pop the value in the heap with the smallest path key, and return the key of it.

```
  def networkDelayTime(self, times: List[List[int]], n: int, k; int) -> int:
    edges = collection.defaultdict(list)
    for u, v, w in times:
      edges[u].append((v,w))

    minHeap = [(0,k)]
    visit = set()
    t = 0
    while minHeap:
      w1, n1 = heapq.heappop(minHeap)
      if n1 in visit: # already been visited?
        continue
      visit.add(n1)
      t = max(t, w1) # w1 is the weight (path cost)

      for n2, w2 in edges[n1]:
        if n2 not in visit: # not visited yet?
          heapq.heappush(minHeap, (w1 + w2, n2))
    return t if len(visit) == n else -1
```

## Practice
**The only way to get better at programming is to practice!**

Reading and learning about these data structures and algorithms is fine, but you can only understand where to apply them through practice. Building an intuition for which data structures/algorithms to use for a given problem can only be done by trying (and failing) lots of other, similar problems. Getting good practice in will be extremely useful for internships/placement assessments.

Links:
[Leetcode](https://leetcode.com/problemset/all/)
[Hackerrank](https://hackerrank.com)
[Awesome Algorithms](https://github.com/tayllan/awesome-algorithms)