---
layout: post
title:  "[Codesignal] 코드시그널 intro 17~20 문제 풀이"
date:   2020-06-08 11:24:39
author: zeroaan
categories: codesignal
# tags: python code
# cover:  "/assets/header_image.jpg"
---

#### 17. arrayChange.py
: You are given an array of integers. On each move you are allowed to increase exactly one of its element by one. Find the minimal number of moves required to obtain a strictly increasing sequence from the input.

**not pass**
```python
def arrayChange(inputArray):

```

<br>

#### 18. palindromeRearranging.py
:  Given a string, find out if its characters can be rearranged to form a palindrome.

```python
def palindromeRearranging(inputString):
    list1 = list(set(inputString))
    value = 0
    for i in list1:
        if inputString.count(i) % 2 == 1:
            value += 1
    return value <= 1
```

<br>

#### 19. areEquallyStrong.py
:  Call two arms equally strong if the heaviest weights they each are able to lift are equal.

Call two people equally strong if their strongest arms are equally strong (the strongest arm can be both the right and the left), and so are their weakest arms. 

Given your and your friend's arms' lifting capabilities find out if you two are equally strong.

```python
def areEquallyStrong(yourLeft, yourRight, friendsLeft, friendsRight):
    return sorted([yourLeft, yourRight]) == sorted([friendsLeft, friendsRight])
```

<br>

#### 20. arrayMaximalAdjacentDifference.py
: Given an array of integers, find the maximal absolute difference between any two of its adjacent elements.

```python
def arrayMaximalAdjacentDifference(inputArray):
    abs_list = []
    for i in range(len(inputArray)-1):
        abs_list.append(abs(inputArray[i]-inputArray[i+1]))
    return max(abs_list)
```