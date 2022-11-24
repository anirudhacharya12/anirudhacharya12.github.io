---
layout: post
title: "Python Decorators and Memoization"
date: 2014-12-04
---

<style>body {text-align: justify}</style>

Decorator classes are a very neat way of wrapping functions within other functions to add meta or additional functionality. Like for example if we are trying to write a recursive solution to a problem and we want to memoize the values that we are calculating so that later we do not have to reevaluate those values we can use the decorator classes. Following problem demonstrates this.

Problem - Given a number, it can be expressed as a sequence of sum of squares of integers. There are many such sequences possible, find out the minimum length among all such sequences.

Example - For number 12, it can be expressed as
```
9+1+1+1
4+4+4
1+1+1+1+1+1+1+1+1+1+1+1
```

Among these the minimum sequence length is 3 for the sequence 4+4+4.

The solution to the problem is

```python
func(N) = min[ func(N-(i^2)) + 1  for all i belonging to [1, floor_of( sqrt(N) ) ] ]
```

The following code solves the above problem -

```python
import math
import functools
def isPerfectSquare(N):
    temp = math.sqrt(N)
    if temp==int(temp):
        return 1
    else:
        return 0
    
class memoize:
    def __init__(self, f):
        self.f = f
        self.cache = {}
    def __call__(self, *args):
        if args not in self.cache:
            self.cache[args] = self.f(*args)
        return self.cache[args]

@memoize
def func(N):
    if isPerfectSquare(N):
        return 1
    num = int(math.sqrt(N))
    i=1
    listA =[]
    while i<=num:
        listA.append(N-(i**2))
        i+=1
    
    vals = map(recurse,listA)
    seqLength = functools.reduce(min,vals)
    return seqLength

def recurse(N):
    return func(N)+1

print func(123)
```

The memoize class is the decorator class, every time the function func is called it first checks if the value has not already been calculated and stored in the cache, and returns the cached value if is pre-computed else it computes the value and stores it in the cache for future reference.