---
layout: post
title:  "[Codesignal] 코드시그널 intro 31~33 문제 풀이"
date:   2020-07-20 18:01:33
author: zeroaan
categories: codesignal
# tags: python code
# cover:  "/assets/header_image.jpg"
---

#### 31. depositProfit.py
: You have deposited a specific amount of money into your bank account. Each year your balance increases at the same growth rate. With the assumption that you don't make any additional deposits, find out how long it would take for your balance to pass a specific threshold.

```python
def depositProfit(deposit, rate, threshold):
    count = 0

    while(deposit < threshold):
        deposit += deposit * (rate/100)
        count += 1
    return count
```

<br>

#### 32. absoluteValuesSumMinimization.py
:  Given a sorted array of integers a, your task is to determine which element of a is closest to all other values of a. In other words, find the element x in a, which minimizes the following sum:

```python
def absoluteValuesSumMinimization(a):
    result = []
    for i in a:
        value = 0
        for j in a:
            value += abs(j-i)
        result.append(value)
    return a[result.index(min(result))]
```

<br>

#### 33. stringsRearrangement.py
:  Given an array of equal-length strings, you'd like to know if it's possible to rearrange the order of the elements in such a way that each consecutive pair of strings differ by exactly one character. Return true if it's possible, and false if not.

Note: You're only rearranging the order of the strings, not the order of the letters within the strings!

#### not pass
```python

```