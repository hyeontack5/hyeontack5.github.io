---
title: "[Algorithm] 팩토리얼 구하기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - 알고리즘
  - 팩토리얼
toc: true
toc_sticky: true
toc_label: "[Algorithm] 팩토리얼 구하기"
toc_icon: "bookmark"
---

# 팩토리얼(Factorial) 구하기

## for문을 이용한 팩토리얼 구하는 알고리즘
1부터 n까지 연속한 숫자를 차례로 곱한 값, 팩토리얼(factorial)을 구하는 문제입니다.

```
num = int(input())

def fact(n):
  result = 1
  for i in range(1, n+1):
    result = result * i # result *= i
  return result

print(fact(num))
```

계산 복잡도는 O(n)

## 재귀 호출을 이용한 팩토리얼 구하는 알고리즘

```
num = int(input())

def fact(n):
  if n <= 1:
    return 1
  return n * fact(n-1)

print(fact(num))
```

계산 복잡도는 O(n)

# 연습문제

## 1부터 n까지의 합 구하기를 재귀 호출로 만들기

입력한 숫자 부터 내림차순으로 덧셈

```
num = int(input())

def sum(n):
  if n <= 1:
    return n
  return sum(n-1) + n

print(sum(num))
```

## 숫자 n개 중에서 최댓값 찾기를 재귀 호출로 만들기

```
def find_max(a, n):
  if n == 1:
    return a[0]
  max_n_1 = find_max(a, n-1)
  if max_n_1 > a[n-1]:
    return max_n_1
  else:
    return a[n-1]
    
v = [17, 92, 18, 33, 58, 7, 33, 42]
print(find_max(v, len(v)))
```