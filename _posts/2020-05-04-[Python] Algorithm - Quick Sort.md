---
layout: post
title:  "[Python] Algorithm - Quick Sort"
date:   2020-05-04 21:18:32
author: zeroaan
categories: python
# tags: python code
# cover:  "/assets/header_image.jpg"
---

## 정렬의 종류에는 선택 정렬, 버블 정렬, 삽입 정렬 등 여러 가지 방법의 정렬이 있습니다.

## 많은 정렬 중에 하나인 퀵 정렬은 다른 정렬보다 빠른 속도로 정렬을 해주고 평균적으로 가장 좋은 성능을 가져 가장 많이 사용되는 정렬 알고리즘입니다.

### 퀵 정렬은 이러한 과정으로 진행합니다.

- 입력된 리스트 안에 한 원소를 기준 원소로 선택합니다.
- 기준 원소를 기준으로 작은 값은 왼쪽으로 큰 값은 오른쪽으로 배치합니다.
- 재배치된 왼쪽 부분 배열과 오른쪽 부분 배열에서도 기준 원소를 정하여 정렬을 진행합니다.
- 이 과정을 계속 반복하여 리스트의 변화가 없으면 정렬이 완료됩니다.

```python
def quicksort(arr):
  if len(arr) > 1:
    value = arr[0] # 배열의 첫 번째 값을 기준 원소로 선택했다.
    left, right = [], [] # 왼쪽, 오른쪽으로 배열을 재배치 하기 위해 리스트를 만들어준다.
    for i in arr[1:]:
      if i < value:
        left.append(i) # 기준 원소보다 작으면 왼쪽 배열에 배치해준다.
      else: 
        right.append(i) # 기준 원소보다 크면 오른쪽 배열에 배치해준다.
    return quicksort(left) + [value] + quicksort(right) # 기준 원소를 중심으로 양쪽으로 나눈 후, 두 개의 배열을 재귀적으로 호출하면 쉽게 해결이 된다.
  else: return arr
```
print(quicksort([8, 3, 5, 1, 9, 7, 2, 4, 6])) = `[1, 2, 3, 4, 5, 6, 7, 8, 9]`