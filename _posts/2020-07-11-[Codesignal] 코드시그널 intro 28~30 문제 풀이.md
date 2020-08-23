---
layout: post
title:  "[Codesignal] 코드시그널 intro 28~30 문제 풀이"
date:   2020-07-11 10:25:24
author: zeroaan
categories: codesignal
# tags: python code
# cover:  "/assets/header_image.jpg"
---

#### 28. alphabeticShift.py
: Given a string, your task is to replace each of its characters by the next one in the English alphabet; i.e. replace a with b, replace b with c, etc (z would be replaced by a).

```python
def alphabeticShift(inputString):
    # print(ord('a')) # 97
    # print(ord('z')) # 122
    
    result = ""
    for i in range(len(inputString)):
        if inputString[i] == 'z':
            result += 'a'
        else:
            result += chr(ord(inputString[i]) + 1)
    return result
```

<br>

#### 29. chessBoardCellColor.py
:  Given two cells on the standard chess board, determine whether they have the same color or not.

```python
def chessBoardCellColor(cell1, cell2):
    # black = list('ACEG')
    # white = list('BDFH')

    # if (cell1[0] in black and cell2[0] in black) or (cell1[0] in white and cell2[0] in white):
    #     return (int(cell1[1]) + int(cell2[1])) % 2 == 0
    # else:
    #     return (int(cell1[1]) + int(cell2[1])) % 2 != 0

    # print(ord("A")) # 65
    return (ord(cell1[0]) + int(cell1[1]) + ord(cell2[0]) + int(cell2[1])) % 2 == 0
```

<br>

#### 30. circleOfNumbers.py
:  Consider integer numbers from 0 to n - 1 written down along the circle in such a way that the distance between any two neighboring numbers is equal (note that 0 and n - 1 are neighboring, too).

Given n and firstNumber, find the number which is written in the radially opposite position to firstNumber.

```python
def circleOfNumbers(n, firstNumber):
    # if firstNumber < n//2:
    #     return firstNumber + n//2
    # return firstNumber - n//2

    return firstNumber + n//2 if firstNumber < n//2 else firstNumber - n//2
```