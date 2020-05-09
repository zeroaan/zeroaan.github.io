---
layout: post
title:  "[Codesignal] 코드시그널 intro 08~10 문제 풀이"
date:   2020-05-09 15:17:55
author: zeroaan
categories: codesignal
# tags: python code
# cover:  "/assets/header_image.jpg"
---

#### 08. matrixElementsSum.py
: After becoming famous, the CodeBots decided to move into a new building together. Each of the rooms has a different cost, and some of them are free, but there's a rumour that all the free rooms are haunted! Since the CodeBots are quite superstitious, they refuse to stay in any of the free rooms, or any of the rooms below any of the free rooms.

```python
def matrixElementsSum(matrix):
    value = 0
    zero = []
    for i in range(len(matrix)):
        for j in range(len(matrix[0])):
            if matrix[i][j] == 0:
                zero.append(j)
            if j not in zero:
                value += matrix[i][j]
    return value
```

<br>

#### 09. allLongestStrings.py
: Given an array of strings, return another array containing all of its longest strings.

```python
def allLongestStrings(inputArray):
    value, result = [], []
    for i in inputArray:
        value.append(len(i))
    for j in range(len(inputArray)):
        if max(value) == value[j]:
            result.append(inputArray[j])
    return result
```

처음에는 위 코드처럼 풀었지만 list comprehension을 알고나서 다음과 같이 코드를 변경하였다.

```python
def allLongestStrings(inputArray):
    longest = max([len(i) for i in inputArray])
    return [j for j in inputArray if len(j) == longest]
```

<br>

#### 10. commonCharacterCount.py
: Given two strings, find the number of common characters between them.

```python
def commonCharacterCount(s1, s2):
    value = 0
    set1 = set(s1) # 중복값 없애기 위해 set 사용
    for i in set1:
        count1 = s1.count(i)
        count2 = s2.count(i)
        value += min(count1, count2)
    return value
```

9번과 마찬가지로 list comprehension으로 다시 풀어보았다.

```python
def commonCharacterCount(s1, s2):
    return sum([min(s1.count(i), s2.count(i)) for i in set(s1)])
```