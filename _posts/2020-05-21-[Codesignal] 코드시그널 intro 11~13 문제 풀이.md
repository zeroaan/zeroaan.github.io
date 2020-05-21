---
layout: post
title:  "[Codesignal] 코드시그널 intro 11~13 문제 풀이"
date:   2020-05-21 13:22:58
author: zeroaan
categories: codesignal
# tags: python code
# cover:  "/assets/header_image.jpg"
---

#### 11. isLucky.py
: Ticket numbers usually consist of an even number of digits. A ticket number is considered lucky if the sum of the first half of the digits is equal to the sum of the second half.

```python
    str_n = str(n)
    mid = len(str_n) // 2
    left = str_n[:mid]
    right = str_n[mid:]
    val_1, val_2 = 0, 0
    for i in left:
        val_1 += int(i)

    for j in right:    
        val_2 += int(j)
    
    if val_1 == val_2:
        return True
    return False
```

list comprehension을 사용하여 다음과 같이 코드를 변경하였다.

```python
def isLucky(n):
    list_n = [int(i) for i in str(n)]
    mid = len(list_n) // 2

    return sum(list_n[:mid]) == sum(list_n[mid:])
```

<br>

#### 12. sortbyHeight.py
: Some people are standing in a row in a park. There are trees between them which cannot be moved. Your task is to rearrange the people by their heights in a non-descending order without moving the trees. People can be very tall!

```python
def sortByHeight(a):
    height = [i for i in a if i > 0]
    
    result = []
    for i in range(len(a)):
        if a[i] == -1:
            result.append(-1)
        else:
            result.append(min(height))
            height.remove(min(height))

    return result
```

<br>

#### 13. reverseInParentheses.py
: Write a function that reverses characters in (possibly nested) parentheses in the input string. Input strings will always be well-formed with matching ()s.

```python
def reverseInParentheses(inputString):
    for i in range(len(inputString)):
        if inputString[i] == "(":
            left = i
        elif inputString[i] == ")":
            right = i
            return reverseInParentheses(inputString[:left] \
            + inputString[left+1:right][::-1] + inputString[right+1:])
    return inputString
```