---
title: "[Network] 간단한 프로토콜 HTTP"
excerpt: "<!--more-->"
categories:
  - Network
tags:
  - Network
  - 그림으로 배우는 HTTP & Network Basic
toc: true
toc_sticky: true
toc_label: "[Network] 간단한 프로토콜 HTTP"
toc_icon: "bookmark"
---

# HTTP는 클라이언트와 서버 간에 통신

- TCP/IP에 있는 HTTP는 클라이언트와 서버 간에 통신을 함
- HTTP 프로토콜에서 반드시 한 쪽이 클라이언트, 다른 한 쪽은 서버

> 클라이언트(Client) : 리소스(텍스트, 이미지 등)을 요구하는 쪽
<br>서버(Server) : 리소스를 제공하는 쪽

# 리퀘스트와 리스폰스

- 클라이언트 측에서 리퀘스트를 보내고, 서버 측에서 리스폰스를 보냄
- 서버 측은 클라이언트의 리퀘스트가 와야지만 리스폰스를 보낼 수 있음

> 리퀘스트(Request) = 요청
<br>리스폰스(Response) = 응답

## 리퀘스트 메시지

<img src="/images/network/geulim-http/request-message-conf.png" width="500" height="300"/>

- **메소드** : 서버에서 요구하는 메소드 종류
- **URI** : 서버 상에 있는 리소스, **리퀘스트 URI** 라고 함
- **프로토콜 버전** : 클라이언트 기능 식별, HTTP 버전
- **리퀘스트 헤더 필드** -> 옵션
- **엔티티** -> 옵션

## 리스폰스 메시지

<img src="/images/network/geulim-http/response-message-conf.png" width="500" height="300"/>

- **프로토콜 버전** : 서버의 HTTP 버전
- **상태 코드** : 리퀘스트의 처리 결과 숫자코드
- **상태 코드 설명** : **프레이즈**라고도 함
- **리스폰스 헤더 필드** -> 옵션
- **바디(body)** : 리소스 본체 -> 옵션

# HTTP는 상태를 유지하지 않는 프로토콜

- HTTP는 상태를 계속 유지하지 않는 **스테이트리스(stateless) 프로토콜**
- 과거의 리퀘스트나 리스폰스 정보를 가지고 있지 않음
- 웹이 진화하면서 상태 유지 필요성이 생김 -> ex) 로그인
  - 상태 유지를 위해 **쿠키(Cookie)** 기술이 도입

# 리퀘스트 URI로 리소스를 식별

- HTTP는 URI를 사용하여 인터넷 상의 리소스를 지정

> URI(Uniform Resource Identifiers)

## 리퀘스트 URI 지정하는 방법

- **특정 리소스에 리퀘스트** 하는 경우

<img src="/images/network/geulim-http/request-uri.png" width="500" height="300"/>

- 특정 리소스가 아닌 **서버 자신에게 리퀘스트** 하는 경우
  - 리퀘스트 URI에 [*]을 지정

```
OPTIONS * HTTP/1.1
```

# 서버에 임무를 부여하는 HTTP 메소드

## HTTP/1.1에서 사용할 수 있는 메소드

- **GET : 리소스 획득**
  - 리퀘스트 URI로 식별된 리소스를 가져오도록 요구
  - 리소스 내용은 서버가 해석한 결과
- **POST : 엔티티 전송**
  - 엔티티를 전송하기 위해 사용
- **PUT : 파일전송**
  - 파일 전송을 위해 사용
  - 엔티티를 리퀘스트 URI에 지정된 곳에 **저장**하도록 요구
  - 인증 기능이 없어서 보안 상의 문제 -> 웹사이트 사용X
- **HEAD : 메시지 헤더 취득**
  - GET과 같은 기능이지만 메시지 바디를 돌려주지 않음
  - URI 유효성과 리소스 갱신 시간 **상태확인하는 목적**으로 이용
- **DELETE : 파일 삭제**
  - PUT과 반대, 리퀘스트 URI로 지정된 리소스 **삭제**하도록 요구
  - PUT과 같이 인증기능X -> 웹사이트 사용X
- **OPTIONS : 제공하고 있는 메소드의 문의**
  - 리퀘스트 URI로 지정한 리소스가 제공하는 메소드 조사를 위해 사용
- **TRACE : 경로 조사**
  - 웹 서버에 접속해 자신에게 통신을 되돌려 받는 루프백(loop-back)을 발생
  - 크로스 사이트 트레이싱(XST)과 같은 공격을 일으킴 
    - -> 보안 문제, TRACE 사용 안함
- **CONNECT : 프록시에 터널링 요구**
  - 프록시에 터널 접속 확립을 요함으로써, TCP 통신을 터널링 시키기 위해 사용
  - SSL이란 TLS 등의 프로토콜로 암호화된 것을 터널링 시키기 위해 사용

# 메소드를 사용해서 지시를 내린다

- 메소드 : 리소스에 어떠한 행동을 하도록 지시하는 역할
  - 메소드는 대소문자를 구별함 -> **대문자로 기재**

# 지속 연결로 접속량을 절약

- HTTP 초기 버전에는 리퀘스트 보낼 때마다 TCP 연결/종료를 함
  - 매번 연결과 종료를 해서 통신량이 늘어남

<img src="/images/network/geulim-http/early-http.png" width="500" height="300"/>

## 지속 연결(Persistent Connections)

- TCP 연결 문제를 해결하기 위한 방법
- 어느 한 쪽이 연결을 종료하지 않는 이상 TCP 연결을 유지
- TCP 연결/종료 반복시 발생하는 **오버헤드 감소**
  - 오버헤드 감소 -> **빠른 req/res 가능** ex) 웹페이지 빨리 표시
- 서버에 대한 **부하 감소**

<img src="/images/network/geulim-http/persistent-connections.png" width="500" height="300"/>

## 파이프라인화(HTTP pipelining)

- req 송신 후 res **기다릴 필요 없이** 바로 req 가능
- 여러 req를 병렬적으로 전송 가능

<img src="/images/network/geulim-http/http-pipelining.png" width="500" height="300"/>

# 쿠키를 사용한 상태 관리

- 스테이트리스(stateless) 프로토콜 이점
  - 서버의 CPU or 메모리같은 리소스의 소비 억제
- **쿠키(Cookie)** : req, res에 쿠키 정보를 추가해서 클라의 상태파악 가능
- 서버에서 res로 **헤드필드에 Set-Cookie**의해 쿠키를 클라에 보존하게 함

<img src="/images/network/geulim-http/cookie-state-management.png" width="500" height="300"/>

# 느낀점

엔티티에 무슨 내용을 들어가게 되는지 모르겠다.
TRACE , CONNECT메소드에 대해 이해가 안가는 부분이 있어서 보충적으로 봐야될듯 하다
지속연결과 파이프라인이 별개인건지 아니면 지속연결에서 옵션으로 추가된게 파이프라인인지 궁금하다.
서버에서 set-cookie에 담아서 보내는데 클라이언트가 그거를 저장하는 기간이 있는지 알아봐야겠다.

# reference

> [그림으로 배우는 HTTP & Network Basic](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=51908132)