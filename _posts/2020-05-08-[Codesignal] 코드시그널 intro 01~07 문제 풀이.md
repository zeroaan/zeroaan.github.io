---
layout: post
title:  "[Codesignal] 코드시그널 intro 01~07 문제 풀이"
date:   2020-05-08 10:46:20
author: zeroaan
categories: codesignal
# tags: python code
# cover:  "/assets/header_image.jpg"
---

#### 01. add.py
: Write a function that returns the sum of two numbers.

```python
def add(param1, param2):
    return param1 + param2
```

<br>

#### 02. centuryFromYear.py
: Given a year, return the century it is in. The first century spans from the year 1 up to and including the year 100, the second - from the year 101 up to and including the year 200, etc.

```python
def centuryFromYear(year):
    return (year-1)//100 + 1
```

<br>

#### 03. checkPalindrome.py
: Given the string, check if it is a palindrome.

```python
def checkPalindrome(inputString):
    value = ''
    for i in range(len(inputString)-1, -1, -1):
       value += inputString[i]
    if inputString == value:
        return True
    return False
```

<br>

#### 04. adjacentElementsProduct.py
: Given an array of integers, find the pair of adjacent elements that has the largest product and return that product.

```python
def adjacentElementsProduct(inputArray):
    value = inputArray[0] * inputArray[1]
    for i in range(1, len(inputArray)-1):
        if inputArray[i] * inputArray[i+1] > value:
            value = inputArray[i] * inputArray[i+1]
    return value
```

<br>

#### 05. shapeArea.py
: Below we will define an n-interesting polygon. Your task is to find the area of a polygon for a given n.

```python
def shapeArea(n):
    return n**2 + (n-1)**2
```

<br>

#### 06. makeArrayConsecutive2.py
: Ratiorg got statues of different sizes as a present from CodeMaster for his birthday, each statue having an non-negative integer size. Since he likes to make things perfect, he wants to arrange them from smallest to largest so that each statue will be bigger than the previous one exactly by 1. He may need some additional statues to be able to accomplish that. Help him figure out the minimum number of additional statues needed.

```python
def makeArrayConsecutive2(statues):
    value = 0
    for i in range(min(statues), max(statues)+1):
        if i not in statues:
            value += 1
    return value
```

<br>

#### 07. almostIncreasingSequence.py *(not pass)*
: Given a sequence of integers as an array, determine whether it is possible to obtain a strictly increasing sequence by removing no more than one element from the array.
<br>
#### *not pass*
```python
def almostIncreasingSequence(sequence):
    a = 0
    for i in range(len(sequence)-1):
        if sequence[i]>=sequence[i+1]:
            a += 1
    if a > 1:
        return False
    return True  
```
<br>
#### *(solution)*
```python
def almostIncreasingSequence(sequence):
    count_decreasing_sq = 0
    for i in range(len(sequence) - 1):
        if sequence[i+1] <= sequence[i]:
            count_decreasing_sq += 1
            if (i >= 1) and (sequence[i+1] <= sequence[i-1]):
                if (len(sequence) - 2 > i) and (sequence[i+2] <= sequence[i]):
                    count_decreasing_sq += 1
        if count_decreasing_sq > 1:
            return False
    return True
```