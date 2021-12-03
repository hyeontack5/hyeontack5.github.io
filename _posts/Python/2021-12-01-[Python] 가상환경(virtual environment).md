---
title: "[Python] 가상환경(virtual environment)"
excerpt: "<!--more-->"
categories:
  - Python
tags:
  - Python
  - 가상환경
toc: true
toc_sticky: true
toc_label: "[Python] 가상환경(virtual environment)"
toc_icon: "bookmark"
---

# 가상환경을 사용하는 이유

- 독립된 공간을 만들어주는 기능을 합니다.
- 필요한 라이브러리만 담아 놓을 수 있는 바구니라고 생각하면 됩니다.
- 프로젝트 A와 B 각각 가상 환경을 만들어 프로젝트 A에는 패키지 버전 A를 설치하고, 프로젝트 B에는 패키지 버전 B을 설치해 독립적으로 관리할 수 있습니다.
- 작업환경이 바뀌게 되더라도 필요한 패키지들을 동일한 버전으로 설치해 작업할 수 있습니다.
  - ex) 컴퓨터를 교체하는 경우

<img src="/images/python/virtual-environment-architecture.png" width="600"/>



# Reference

> [파이썬에서 venv로 가상 환경 사용하기](https://www.daleseo.com/python-venv/)<br>
[[Python] 가상환경](https://medium.com/@psychet_learn/python-%EA%B0%80%EC%83%81%ED%99%98%EA%B2%BD-a87fc6e4d12b)<br>
[python virtual environment setup in ubuntu](https://django-easy-tutorial.blogspot.com/2015/08/python-virtual-environment-setup-in-ubuntu.html)<br>
[python의 가상환경](https://velog.io/@full_accel/python-%EA%B0%80%EC%83%81%ED%99%98%EA%B2%BD)