---
title: "[Algorithm] 절대값"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - 알고리즘
  - 절대값
toc: true
toc_sticky: true
toc_label: "[Algorithm] 절대값"
toc_icon: "bookmark"
---

# 절대값 구하기 알고리즘

## if문을 이용한 절대값 구하기

```
def abs_sign(a):
  if a >= 0:
    return a
  else:
    return -a

print(abs_sign(5))
print(abs_sign(-3))
```

## 제곱근을 이용한 절대값 구하기

```
import math # 수학 모듈 사용

def abs_square(a):
  b = a * a
  return math.sqrt(b) # 수학 모듈의 제곱근 함수

print(abs_square(5))
print(abs_square(-3))
```