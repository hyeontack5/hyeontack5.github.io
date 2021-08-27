---
title: "[Algorithm] 최대값 찾기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - 알고리즘
  - 최대값 찾기
toc: true
toc_sticky: true
toc_label: "[Algorithm] 최대값 찾기"
toc_icon: "bookmark"
---

# 최대값을 구하는 알고리즘

리스트 [17, 92, 18, 33, 58, 7, 33, 42] 중에서 **최대값**을 찾는 알고리즘

```
def find_max(n):
  max = n[0]
  for i in range(0, len(n)):
    if n[i] >= max:
      max = n[i]
  return max

number_list = [17, 92, 18, 33, 58, 7, 33, 42]
print(find_max(number_list))
```

계산 복잡도는 O(n)

# 최대값의 위치를 구하는 알고리즘

리스트 [17, 92, 18, 33, 58, 7, 33, 42] 중에서 가장 큰 값이 있는 **위치 번호**를 돌려주는 알고리즘

```
def find_max_idx(n):
  max_idx = 0
  for i in range(0, len(n)):
    if n[i] >= n[max_idx]:
      max_idx = i
  return max_idx

number_list = [17, 92, 18, 33, 58, 7, 33, 42]
print(find_max_idx(number_list))
```

# 연습문제

## 최솟값을 구하는 알고리즘

숫자 n개를 리스트로 입력받아 최솟값을 구하는 프로그램을 만들기

```
def find_min(n):
  min = n[0]
  for i in range(0, len(n)):
    if min >= n[i]:
      min = n[i]
  return min

number_list = [17, 92, 18, 33, 58, 7, 33, 42]
print(find_min(number_list))
```

## 최솟값의 위치를 구하는 알고리즘

숫자 n개를 리스트로 입력받아 최솟값이 있는 위치번호를 알려주는 프로그램을 만들기

```
def find_min_idx(n):
  min_idx = 0
  for i in range(0, len(n)):
    if n[min_idx] >= n[i]:
      min_idx = i
  return min_idx

number_list = [17, 92, 18, 33, 58, 7, 33, 42]
print(find_min_idx(number_list))
```