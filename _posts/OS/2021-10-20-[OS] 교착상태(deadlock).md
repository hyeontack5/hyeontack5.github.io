---
title: "[OS] 교착상태(deadlock)"
excerpt: "<!--more-->"
categories:
  - OS
tags:
  - OS
  - 데드락
  - deadlock
toc: true
toc_sticky: true
toc_label: "[OS] 교착상태(deadlock)"
toc_icon: "bookmark"
---

# The Deadlock problem

**Deadlock**

- 일련의 프로세스들이 서로가 가진 자원을 기다리며 block된 상태

**Resource(자원)**

- 하드웨어, 소프트웨어 등을 포함하는 개념
- ex) I/O device, CPU cycle, memory space, semaphore 등
- 프로세스가자원을 사용하는 절차
  - Request(요청), Allocate(할당), Use(사용), Release(배포)

**Deadlock Example 1**

- 시스템에 2개의 tape drive가 있음
- 프로세스 P1과 P2 각각이 하나의 tape drive를 보유한 채 다른 하나를 기다리고 있음

**Deadlock Example 2**

- Binary semaphores A and B

```c
P0       P1
P(A);    P(B);
P(B);    P(A);
```

# Deadlock 발생의 4가지 조건

_1._ **Mutual exclusion(상호 배제)**

- 매 순간 하나의 프로세스만이 자원을 사용할 수 있음

_2._ **No preemption(비선점)**

- 프로세스는 자원을 스스로 내어놓을 뿐 강제로 빼앗기지 않음

_3._ **Hold and wait(보유 대기)**

- 자원을 가진 프로세스가 다른 자원을 기다릴 때 보유 자원을 놓지 않고 계속 가지고 있음

_4._ **Circular wait(환형 대기)**

- 자원을 기다리는 프로세스간에 사이클이 형성되어야 함
- 프로세스 P0, P1 ... Pn이 있을 때

```c
P0은 P1이 가진 자원을 기다림
P1은 P2가 가진 자원을 기다림
Pn-1은 Pn이 가진 자원을 기다림
Pn은 P0이 가진 자원을 기다림
```

# Resource-Allocation Graph (자원할당 그래프) -> deadlock 판별 방법

- 자원에서 프로세스로 가는 화살표의 의미
  - 자원을 프로세스가 점유하고 있다는 뜻
- 프로세스에서 자원으로 가는 화살표
  - 프로세스가 자원을 기다리고 있는다는 뜻
- 자원 안에 점의 의미
  - 자원 안에 인스턴스의 갯수

**Vertex**

- Process = {P1, P2, ..., Pn}
  - 그림에서 동그라미
- Resource = {R1, R2, ..., Rm}
  - 그림에서 사각형

**Edge**

- request edge Pi -> Rj
- assignment edge Rj -> Pi

- 그래프에 cycle이 없으면 deadlock이 아님
- 그래프에 cycle이 있으면
  - if **only one instance** per resoure type, then **deadlock**
  - if several instances per resource type, possibility of deadlock
- 왼쪽 그림에서 P1 부터 시작해서 다시 P1으로 돌아오는 cycle 한 개가이 있고 P2부터 시작해서 다시 P2로 돌아오는 cycle이 존재함, R2 자원의 인스턴스가 2개 이지만 모두 cycle로 형성 되어 있기 때문에 deadlock 임
- 오른쪽의 그림은 P1부터 시작해서 cycle은 있지만 R1과 R2의 자원에 인스턴스가 2개씩 있기 때문에 deadlock이 아님 나머지 하나의 인스턴스는 사이클과 무관하게 동작하고 있음

# Deadlock의 처리 방법

_1._ **Deadlock Prevention**

- 자원 할당 시 Deadlock의 4가지 필요 조건 중 어느 하나가 만족되지 않도록 하는 것

_2._ **Deadlock Avoidance**

- 자원 요청에 대한 부가적인 정보를 이용해서 deadlock의 가능성이 없는 경우에만 자원을 할당
- 시스템 state가 원래 state로 돌아올 수 있는 경우에만 자원 할당

_3._ **Deadlock Detection and recovery**

- Deadlock 발생은 허용하되 그에 대한 detection 루틴을 두어 deadlock 발견시 recover

_4._ **Deadlock Ignorance**

- Deadlock을 시스템이 책임지지 않음
- UNIX를 포함한 대부분의 OS가 채택

- 1번과 2번은 deadlock이 안생기게 미연에 방지하는 방법
- 3번과 4번은 deadlock이 생기든지 말든지 내비둠

## Deadlock Prevention

**Mutual Exclusion**

- 공유해서는 안되는 자원의 경우 반드시 성립해야 함

**Hold and wait**

- 프로세스가 자원을 요청할 때 어떤 자원도 가지고 있지 않음
- 방법 1. 프로세스 시작 시 모든 필요한 자원을 할당 받게 하는 방법
- 방법 2. 자원이 필요할 경우 보유 자원을 모두 놓고 다시 요청

**No Preemption**

- process가 어떤 자원을 기다려야 하는 경우 이미 보유한 자원이 선점됨
- 모든 필요한 자원을 얻을 수 있을 때 그 프로세스는 다시 시작
- State를 쉽게 save하고 restore할 수 있는 자원에서 주로 사용 (CPU, memory)

**Circular Wait**

- 모든 자원 유형에 할당 순서를 정하여 정해진 순서대로만 자원 할당
- 예를 들어 순서가 3인 자원 Ri를 보유 중인 프로세스가 순서가 1인 자원 Rj을 할당받기 위해서는 우선 Ri를 release해야 함

-> Utilization 저하, throughput 감소, starvation 문제

## Deadlock Avoidance

**Deadlock avoidance**

- 자원 요청에 대한 부가정보를 이용해서 자원 할당이 deadlock으로 부터 안전(safe)한지를 동적으로 조사해서 안전한 경우에만 할당
- 가장 단순하고 일반적인 모델은 프로세스들이 필요로 하는 각 자원별 최대 사용량을 미리 선언하도록 하는 방법임

**safe state**

- 시스템 내의 프로세스들에 대한 safe sequence가 존재하는 상태

**safe sequence**

- 프로세스의 sequence <P1, P2, ..., Pn>이 safe하려면 Pi(1<= i <=n)의 자원 요청이 가용 자원 + 모든 Pj(j < i)의 보유 자원에 의해 충족되어야 함
- 조건을 만족하면 다음 방법으로 모든 프로세스의 수행을 보장
  - Pi의 자원 요청이 즉시 충족될 수 없으면 모든 Pj(j < i)가 종료될 때까지 기다림
  - Pi-1이 종료되면 Pi의 자원 요청을 만족시켜 수행함

**Deadlock Avoidance**

- 시스템이 safe state에 있으면 -> no deadlock
- 시스템이 unsafe state에 있으면 -> possibility of deadlock
- Deadlock Avoidance
  - 시스템이 unsafe state에 들어가지 않는 것을 보장

2가지 경우의 avoidance 알고리즘

- Single instance per resource types
  - Resource Allocation Graph algorithm 사용
- Multiple instance per resource types
  - Banker's Algorithm 사용

### Resource Allocation Graph algorithm

점선은 한 번 있을 까 말 까한 경우를 표시한 것

점선을 포함해서 사이클이 만들어 질거 같으면 아예 자원을 주지 않음

### Example of Banker's Algorithm

## Deadlock Detection and recovery

**Deadlock Detection**

- Resource type 당 single instance인 경우
  - 자원할당 그래프에서의 cycle이 곧 deadlock을 의미
- Resource type 당 multiple instance인 경우
  - Banker's algorithm과 유사한 방법 활용

**Wait-for graph 알고리즘**

- Resource type 당 single instance인 경우
- Wait-for graph
  - 자원할당 그래프의 변형
  - 프로세스만으로 node 구성
  - Pi가 가지고 있는 자원을 Pk가 기다리는 경우 Pk -> Pi
- Algorithm
  - Wait-for graph에 사이클이 존재하는지를 주기적으로 조사
  - O(n^2)

## Deadlock Ignorance

- Deadlock이 일어나지 않는다고 생각하고 아무런 조치도 취하지 않음
- Deadlock이 매우 드물게 발생하므로 deadlock에 대한 조치 자체가 더 큰 overhead일 수 있음
- 만약, 시스템에 deadlock이 발생한 경우 시스템이 비정상적으로 작동하는 것을 느끼면 직접 process를 죽이는 방법 등으로 대처함
- UNIX, WINDOWS 등 대부분의 범용 OS가 채택함

# reference

> [운영체제 - 이화여자대학교](http://www.kocw.or.kr/home/cview.do?cid=4b9cd4c7178db077)