---
layout: post
title:  "[Codesignal] 코드시그널 intro 25~27 문제 풀이"
date:   2020-06-29 18:47:32
author: zeroaan
categories: codesignal
# tags: python code
# cover:  "/assets/header_image.jpg"
---

#### 25. arrayReplace.py
: Given an array of integers, replace all the occurrences of elemToReplace with substitutionElem.

```python
def arrayReplace(inputArray, elemToReplace, substitutionElem):
    # for i in range(len(inputArray)):
    #     if inputArray[i] == elemToReplace:
    #         inputArray[i] = substitutionElem
    # return inputArray

    return [substitutionElem if i == elemToReplace else i for i in inputArray]
```

<br>

#### 26. evenDigitsOnly.py
:  Check if all digits of the given integer are even.

```python
def evenDigitsOnly(n):
    for i in str(n):
        if int(i) % 2 != 0:
            return False
    return True
```

<br>

#### 27. variableName.py
:  Correct variable names consist only of English letters, digits and underscores and they can't start with a digit.

Check if the given string is a correct variable name.

```python
def variableName(name):
    value = list('abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_')
    
    if name[0] in list('0123456789'):
        return False

    for i in name:
        if i not in value:
            return False
    return True
```