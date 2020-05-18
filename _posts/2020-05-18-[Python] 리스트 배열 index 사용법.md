---
layout: post
title:  "[Python] 리스트 배열 index 사용법"
date:   2020-05-18 14:23:57
author: zeroaan
categories: python
# tags: python code
# cover:  "/assets/header_image.jpg"
---

list 에서 배열의 index에 접근하는 방법이 여러가지 있다.

기본적으로 사용하는 index 접근 방법이다.<br>
`list[A:B] = index A 부터 index B-1 까지`

<br>

```python
>> list = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>> list
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>> list[:3] # 처음부터 index 2 까지
[0, 1, 2]

>> list[5:] # index 5 부터 끝까지
[5, 6, 7, 8, 9]

>> list[4:7] # index 4 부터 index 6 까지
[4, 5, 6]
```

<br>

다음은 더 나아가 거꾸로 출력하는 방법과 간격을 두어 출력하는 방법을 알아보겠다.<br>
```python
>> list = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]


>> list[::-1] # 역순으로 -1칸 간격으로
[9, 8, 7, 6, 5, 4, 3, 2, 1, 0]

>> list[::-2] # 역순으로 -2칸 간격으로
[9, 7, 5, 3, 1]

>> list[::2] # 처음부터 끝까지 2칸 간격으로
[0, 2, 4, 6, 8]

>> list[1::2] # index 1 부터 끝까지 2칸 간격으로
[1, 3, 5, 7, 9]

>> list[5::-1] # index 5부터 역순으로 -1 칸 간격으로
[5, 4, 3, 2, 1, 0]

>> list[3:8:2] # index 3부터 index 7까지 2칸 간격으로
[3, 5, 7]
```