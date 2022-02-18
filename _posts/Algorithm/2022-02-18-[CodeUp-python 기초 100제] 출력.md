---
title: "[CodeUp-python 기초 100제] 출력"
excerpt: "<!--more-->"
categories:
  - Algorithm
tags:
  - Algorithm
  - codeup
  - python 기초 100제
toc: true
toc_sticky: true
toc_label: "[CodeUp-python 기초 100제] 출력"
toc_icon: "bookmark"
---

# 6001 : [기초-출력] 출력하기01

**문제 설명**

python 언어에서 가장 기본적인 명령이 출력문이다.<br>
print( )를 이용해 다음 단어를 출력하시오.

Hello

**출력 예시**

```python
Hello
```

**문제 정답**

```python
print("Hello")
```

**문제 풀이**

- 파이썬은 `print()`를 이용하여 화면에 문자열을 출력할 수 있습니다.

# 6002 : [기초-출력] 출력하기02

**문제 설명**

이번에는 공백( )을 포함한 문장을 출력한다.<br>
다음 문장을 출력해보자.

Hello World<br>
(대소문자에 주의한다.)

**출력 예시**

```python
Hello World
```

**문제 정답**

```python
print("Hello World")
# print("Hello", "World")
```

**문제 풀이**

- `print("문자열1 문자열2")`, `print("문자열1", "문자열2")`은 둘다 공백을 사이에 두고 출력됩니다.
  - 문자열을 공백을 두고 출력할 때는 직접 공백을 주거나 `,`를 사용하려 공백을 출력할 수 있습니다.

# 6003 : [기초-출력] 출력하기03

**문제 설명**

이번에는 줄을 바꿔 출력하는 출력문을 연습해보자.<br>
다음과 같이 줄을 바꿔 출력해야 한다.

Hello<br>
World<br>
(두 줄에 걸쳐 줄을 바꿔 출력)

**출력 예시**

```python
Hello
World
```

**문제 정답**

```python
print("Hello")
print("World")
# print("Hello\nWorld")
```

**문제 풀이**

- `print()`는 출력한 후 마지막에 자동으로 개행문자(new line)이 포함되어 있습니다.
- `\n` 개행문자를 사용하여 줄바꿈을 할 수도 있습니다.

# 6004 : [기초-출력] 출력하기04

**문제 설명**

이번에는 작은 따옴표(')(single quotation mark)가 들어있는 출력문 연습을 해보자.<br>
다음 문장을 출력하시오.

'Hello'

**출력 예시**

```python
'Hello'
```

**문제 정답**

```python
print("'Hello'")
```

# 6005 : [기초-출력] 출력하기05

**문제 설명**

이번에는 큰따옴표(")(double quotation mark)가 포함된 출력문을 연습해보자.<br>
다음 문장을 출력하시오.

"Hello World"<br>
(단, 큰따옴표도 함께 출력한다.)

**출력 예시**

```python
"Hello World"
```

**문제 정답**

```python
print('"Hello World"')
print("\"Hello World\"")
```

**문제 풀이**

- 다른 언어와 다르게 파이썬에서 print()안에 문자열을 넣을 때 작은 따옴표(')(single quotation mark)나 큰 따옴표(")(double quotation mark) 둘다 사용이 가능합니다.
  - 하지만 저는 다른 언어와 헷갈리지 않기 위해 큰 따옴표를 사용하고 있습니다.

# 6006 : [기초-출력] 출력하기06

**문제 설명**

이번에는 특수문자 출력에 도전하자!!<br>
다음 문장을 출력하시오.

"!@#$%^&*()'<br>
(단, 큰따옴표와 작은따옴표도 함께 출력한다.)

**출력 예시**

```python
"!@#$%^&*()'
```

**문제 정답**

```python
print("\"!@#$%^&*()'")
```

**문제 풀이**

- 출력 형식에 필요한 따옴표와 출력할 문자인 따옴표를 구분하기 위하여 `\"` 또는 `\'` 를 이용하여 출력할 수 있습니다.

# 6007 : [기초-출력] 출력하기07

**문제 설명**

윈도우 운영체제의 파일 경로를 출력하는 연습을 해보자.<br>
파일 경로에는 특수문자들이 포함된다.<br>
다음 경로를 출력하시오.

"C:\Download\'hello'.py"<br>
(단, 따옴표도 함께 출력한다.)

**출력 예시**

```python
"C:\Download\'hello'.py"
```

**문제 정답**

```python
print("\"C:\\Download\\'hello'.py\"")
```

**문제 풀이**

- `\` 문자를 출력하기 위해서는 `\\`를 해줘야 합니다.

# 6008 : [기초-출력] 출력하기08

**문제 설명**

출력문 연습의 마지막 문제이다.<br>
(생각과 시도를 많이 해야하는 문제들은 한 두 문제씩 넘겼다가 나중에 풀어보면 된다.)<br>
이번에는 다음과 같은 python프로그램의 소스코드를 출력해보자.<br>

print("Hello\nWorld")<br>
위 코드를 정확히 그대로 출력하시오.(공백문자 주의)

**출력 예시**

```python
print("Hello\nWorld")
```

**문제 정답**

```python
print('print("Hello\\nWorld")')
```

**문제 풀이**

- `\` 문자를 출력하기 위해서는 `\\`를 해줘야 합니다.

# Reference

> [CodeUp-python 기초 100제](https://codeup.kr/problemsetsol.php?psid=33)<br>