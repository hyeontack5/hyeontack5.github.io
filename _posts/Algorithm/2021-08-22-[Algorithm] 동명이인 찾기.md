---
title: "[Algorithm] 동명이인 찾기"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - 알고리즘
  - 동명이인 찾기
toc: true
toc_sticky: true
toc_label: "[Algorithm] 동명이인 찾기"
toc_icon: "bookmark"
---

# 동명이인을 찾는 알고리즘

```
def find_same_name(n):
  result = set()  # 결과를 저장할 빈 집합
  for i in range(0, len(n)-1):
    for j in range(i+1, len(n)):
      if n[i] == n[j]:
        result.add(n[i])
  return result

name = ["Tom", "Jerry", "Mike", "Tom"]
print(find_same_name(name))

name2 = ["Tom", "Jerry", "Mike", "Tom", "Mike"]
print(find_same_name(name2))
```

# 연습문제

n명 중 두명을 뽑아 짝을 짓는다고 할 때 짝을 지을 수 있는 모든 조합을 출력하는 알고리즘을 만들어 보세요.
예를 들어 입력이 리스트 ["Tom", "Jerry", "Mike"]라면 다음과 같은 세 가지 경우를 출력합니다.

```
Tom - Jerry
Tom - Mike
Jerry - Mike
```

```
def print_pairs(n):
  for i in range(0, len(n)-1):
    for j in range(i+1, len(n)):
      print(n[i], "-", n[j])

name = ["Tom", "Jerry", "Mike"]
print_pairs(name)
```