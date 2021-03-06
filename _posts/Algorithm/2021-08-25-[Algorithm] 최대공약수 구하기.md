---
title: "[Algorithm] 최대공약수 구하기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - 최대공약수
  - 유클리드
  - 피보나치 수열
toc: true
toc_sticky: true
toc_label: "[Algorithm] 최대공약수 구하기"
toc_icon: "bookmark"
---

# 최대공약수(Greatest Common Divisor, GCD) 구하기

두 개 이상의 정수의 공통 약수 중에서 가장 큰 값을 의미합니다.
<br>두 수 의 **1.약수** 중에서 **2.공통**된 것을 찾아 그 값 중 **3.최댓값**인 것을 찾으면 됩니다.

## 최대공약수 알고리즘

1. 두 수 중 더 작은 값을 i에 저장
2. i가 두 수의 공통된 약수인지 확인
3. 공통된 약수이면 이 값을 결괏값으로 반환하고 종료
4. 공통된 약수가 아니면 i를 1만큼 감소 시키고 2번으로 돌아가 반복

```python
def gcd(a, b):
  i = min(a, b) # 두 수 중에서 최솟값을 구하는 파이썬 함수
  while True:
    if a % i == 0 and b % i == 0:
      return i
    i = i - 1 # i를 1만큼 감소시킴

print(gcd(1, 5))
print(gcd(3, 6))
```

## 유클리드(Euclid) 알고리즘

* a와 b의 최대공약수는 'b'와 'a를 b로 나눈 나머지'의 최대공약수와 같다.
<br>즉, gcd(a, b) = gcd(b, a%b)

* 어떤 수와 0의 최대공약수는 자기 자신입니다.
<br>즉, gcd(n, 0) = n

`gcd(60, 24) = gcd(24, 60 % 24) = gcd(24, 12) = gcd(12, 24 % 12) = gcd(12, 0) = 12`

a와 b의 최대공약수를 구하기 위해서 (a, b)보다 좀 더 작은 숫자인 (b, a % b)의 최대공약수를 구하는 과정을 이용하는 **전형적인 재귀 호출** 문제입니다.

```python
def gcd(a, b):
  if b == 0:
    return a
  return gcd(b, a % b)

print(gcd(1, 5))
print(gcd(3, 6))
```

# 연습문제 

0과 1부터 시작해서 바로 앞의 두 수를 더한 값을 다음 값으로 추가하는 방식으로 만든 수열을 피보나치 수열이라고 합니다.
즉, 0+1=1, 1+1=2, 1+2=3이므로 피보나치 수열은 다음과 같습니다.

`0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55 ...`

피보나치 수열이 파이썬의 리스트처럼 0번부터 시작한다고 가정할 때 n번째 피보나치 수를 구하는 알고리즘을 **재귀호출**을 이용해서 구현해보기
(힌트: 7번 값 = 5번 값 + 6번 값)

## 재귀없이 피보나치 수열

```python
def make_fibo(num): # 피보나치 수열 만드는 함수
  result = [] # 빈 리스트 생성

  if num > 1:
    first = 0
    second = 1

    result.append(first)
    result.append(second)

    for i in range(2, num):
      third = first + second
      result.append(third)
      first = second
      second = third

  else:
    result.append(0)

  return result

def pick_fibo(result, pick_num):  # n번째 피보나치 수 구하는 함수
  print('선택한 n번째 피보나치 수 : ' + str(result.pop(pick_num)))

num = int(input())  # 파보나치 수열 리스트 길이
pick_num = int(input()) # 피보나치 수열 n번째 피보나치 수
result = make_fibo(num)
pick_fibo(result, pick_num)
```

## 재귀 피보나치 수열

```python
def fibo(n):
  if n <= 1:
    return n
  return fibo(n-1) + fibo(n-2)

printf(fibo(7))
printf(fibo(10)) 
```