---
layout: post
title:  "[Codesignal] 코드시그널 intro 21~24 문제 풀이"
date:   2020-06-24 13:14:03
author: zeroaan
categories: codesignal
# tags: python code
# cover:  "/assets/header_image.jpg"
---

#### 21. isIPv4Address.py
: An IP address is a numerical label assigned to each device (e.g., computer, printer) participating in a computer network that uses the Internet Protocol for communication. There are two versions of the Internet protocol, and thus two versions of addresses. One of them is the IPv4 address.

Given a string, find out if it satisfies the IPv4 address naming rules.

```python
def isIPv4Address(inputString):
    number = inputString.split('.')

    if len(number) != 4:
        return False

    for i in number:
        if i.isdigit() == False:
            return False
        if int(i) < 0 or int(i) > 255:
            return False
        if i == '00' or i == '01': return False
        
    return True
```

<br>

#### 22. avoidObstacles.py
:  You are given an array of integers representing coordinates of obstacles situated on a straight line.

Assume that you are jumping from the point with coordinate 0 to the right. You are allowed only to make jumps of the same length represented by some integer.

Find the minimal length of the jump enough to avoid all the obstacles.

**not pass**
```python
def avoidObstacles(inputArray):
    for i in range(1, 1001):
        value = 0
        for j in inputArray:
            if j % i != 0:
                value += 1
        if value == len(inputArray):
            return i
```

<br>

#### 23. boxBlur.py
:  Last night you partied a little too hard. Now there's a black and white photo of you that's about to go viral! You can't let this ruin your reputation, so you want to apply the box blur algorithm to the photo to hide its content.

The pixels in the input image are represented as integers. The algorithm distorts the input image in the following way: Every pixel x in the output image has a value equal to the average value of the pixel values from the 3 × 3 square that has its center at x, including x itself. All the pixels on the border of x are then removed.

Return the blurred image as an integer, with the fractions rounded down.

```python
def boxBlur(image):
    result = []
    row = len(image)
    col = len(image[0])

    for i in range(1, row-1):
        value = []
        for j in range(1, col-1):
            pixel = 0
            for x in range(i-1, i+2):
                for y in range(j-1, j+2):
                    pixel += image[x][y]
            value.append(pixel//9)
        result.append(value)

    return result
```

<br>

#### 24. minesweeper.py
: In the popular Minesweeper game you have a board with some mines and those cells that don't contain a mine have a number in it that indicates the total number of mines in the neighboring cells. Starting off with some arrangement of mines we want to create a Minesweeper game setup.

```python
def minesweeper(matrix):
    result = []
    row = len(matrix)
    col = len(matrix[0])

    for i in range(row):
        value = []
        for j in range(col):
            mine = 0
            if i > 0:
                if matrix[i-1][j]:
                    mine += 1
            if j > 0:
                if matrix[i][j-1]:
                    mine += 1
            if i > 0 and j > 0:
                if matrix[i-1][j-1]:
                    mine += 1
            if i < row - 1:
                if matrix[i+1][j]:
                    mine += 1
            if j < col - 1:
                if matrix[i][j+1]:
                    mine += 1
            if i < row - 1 and j < col - 1:
                if matrix[i+1][j+1]:
                    mine += 1
            if i > 0 and j < col - 1:
                if matrix[i-1][j+1]:
                    mine += 1
            if i < row - 1 and j > 0:
                if matrix[i+1][j-1]:
                    mine += 1
            value.append(mine)
        result.append(value)
    
    return result
```