---
title: "[Algorithm] 순차 탐색"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - 순차 탐색
toc: true
toc_sticky: true
toc_label: "[Algorithm] 순차 탐색"
toc_icon: "bookmark"
---

# 순차 탐색(Sequential search) 알고리즘

리스트 안에 있는 원소를 하나씩 순차적으로 비교하면서 탐색한다고 하여 **순차 탐색**이라고 합니다. 

첫 번째 자료부터 하나씩 비교하면서 같은 값이 나오면 그 위치를 결과로 돌려주고,
리스트 끝까지 찾아도 같은 값이 나오지 않으면 -1을 돌려주면 됩니다.

```python
def search_list(v, num):
  for i in range(0, len(v)-1):
    if num == v[i]:
      return i

  return -1

v = [17, 92, 18, 33, 58, 7, 33, 42]
print(search_list(v, 18))
print(search_list(v, 33)) # 첫 번째 위치만 결과로 돌려줍니다.
print(search_list(v, 900))
```

계산 복잡도는 O(n)

# 연습문제 

## 리스트에서 특정 숫자의 위치를 전부 찾기

찾는 값이 나오는 모든 위치를 리스트로 돌려주는 탐색 알고리즘을 만들고,
찾는 값이 리스트에 없다면 빈 리스트인 []를 돌려줍니다.

```python
def search_list(v, num):
  result = [] # 새 리스트를 만들어 결괏값을 저장
  for i in range(0, len(v)-1):
    if num == v[i]:
      result.append(i)

  return result

v = [17, 92, 18, 33, 58, 7, 33, 42]
print(search_list(v, 18))
print(search_list(v, 33))
print(search_list(v, 900))
```

계산 복잡도는 O(n)

## 학생 번호에 해당하는 학생 이름 찾기

다음과 같이 학생 번호와 이름이 리스트로 주어졌을 때 학생 번호를 입력하면
학생 번호에 해당하는 이름을 순차 탐색으로 찾아 돌려주는 함수를 만들기.
해당하는 학생 번호가 없으면 물음표(?)를 돌려줍니다.
<br>참고로 학생 번호가 39번이면 "Justin", 14번이면 "John"을 돌려줍니다.

`stu_no = [39, 14, 67, 105]`
<br>`stu_name = ["Justin", "john", "Mike", "Summer"]`

```python
def get_name(stu_no, stu_name, find_num):
  for i in range(0, len(stu_no)):
    if find_num == stu_no[i]:
      return stu_name[i]
  
  return "?"

stu_no = [39, 14, 67, 105]
stu_name = ["Justin", "john", "Mike", "Summer"]

find_num = int(input())
print(get_name(stu_no, stu_name, find_num))
```
