---
title: "[Algorithm] 1부터 n까지의 합"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - 알고리즘
  - 1부터 n까지의 합
toc: true
toc_sticky: true
toc_label: "[Algorithm] 1부터 n까지의 합"
toc_icon: "bookmark"
---

# 1부터 n까지의 합 구하기 

## 방법1

```
def sum(n):
  result = 0
  for i in range(1, n + 1):
    result = result + 1 # result += i
  return result

print(sum(10))
print(sum(100))
```

## 방법2

```
def sum(n):
  return n * (n + 1) // 2

print(sum(10))
print(sum(100))
```

## 연습문제

1부터 n까지 연속한 숫자의 제곱의 합을 구하는 프로그램을 for 반복문으로 만들기
(ex. n = 10이라면 1^2 + 2^2 + 3^2 + ... + 10^2  = 385)

## 방법 1
```
def sum(n):
  result = 0
  for i in range(1, n + 1):
    result = result + (n * n)
    return result

print(sum(10)) 
```

## 방법 2
```
def sum(n):
    return n * (n + 1) * (2 * n + 1) / 6

print(sum(10)) 
```