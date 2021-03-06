---
title: "[Network] HTTP와 연계하는 웹 서버"
excerpt: "<!--more-->"
categories:
  - Network
tags:
  - Network
  - 그림으로 배우는 HTTP & Network Basic
toc: true
toc_sticky: true
toc_label: "[Network] HTTP와 연계하는 웹 서버"
toc_icon: "bookmark"
---

# 5-1. 1대로 멀티 도메인을 가능하게 하는 가상 호스트

- HTTP/1.1에서는 하나의 HTTP 서버에 여러 개의 웹 사이트를 실행할 수 있음 -> **가상 호스트 기능**
- **가상 호스트(Virtual Host)** : 물리적으로 서버가 1대지만 가상으로 여러 대가 있는 것처럼 하는 방식
- HTTP를 사용해 클라가 서버에 액세스할 때 **호스트명**이나 **도메인 명**이 자주 사용됨
  - 도메인 명은 DNS에 의해 IP 주소로 변환됨
  - 결국 리퀘스트가 서버에 도착할 때는 IP 주소로 액세스
- 1대의 서버 안에 같은 IP주소의 웹 서버에 여러 웹 사이트가 있을 때 DNS로 도메인명을 해결하면 어떤 웹사이트에 접근하는지 알 수 없음

**Solution**
- HTTP 리퀘스트 보낼 때 호스트 명과 도메인 명을 완전히 포함한 URI를 지정
- Host 헤더 필드에서 지정

# 5-2. 통신을 중계하는 프로그램 : 프록시, 게이트웨이, 터널

- HTTP는 클라와 서버 이외에 프록시(Proxy), 게이트웨이(Gateway), 터널(Tunnel)와 같은 통신을 중계하는 프로그램과 서버를 연계 가능
  - 이 프로그램과 서버는 그 다음에 있는 서버에 리퀘스트를 중계하고, 그 서버로 부터 받은 리스폰스를 클라에게 반환하는 역할 담당

**프록시**

- 클라이언트와 서버의 양쪽 역할을 하는 중계 프로그램
  - 클라의 리퀘스트를 서버에 전송하고, 서버의 리스폰스를 클라에 전송

**게이트웨이**

- 다른 서버를 중계하는 서버, 클라로부터 수신한 리퀘스트를 리소스를 보유한 서버인 것처럼 수신함
  - 클라는 상대가 게이트웨이라는 것을 알지 못함

**터널**

- 서로 떨어진 두 대의 클라와 서버 사이를 중계하며 접속을 주선하는 중계 프로그램

## 5.2.1 프록시

- 클라로부터 받은 리퀘스트를 다른 서버에 전송하는 역할
  - 클라로부터 받은 리퀘스트 URI를 변경하지 않고 그 다음의 리소스를 가지고 있는 서버로 보냄
  - **오리진 서버(Origin Server)** : 리소스 본체를 가진 서버
  - 오리진 서버로부터 되돌아온 리스폰스는 프록시 서버를 경유해 클라에 돌아옴
- HTTP 통신을 할 때, 프록시 서버 여러 대 경유해서 리퀘스트랑 리스폰스를 중계해 감
  - 중계할 때 Via 헤더 필드에 경유한 호스트 정보를 추가해야함

**프록시 서버 사용하는 이유**

- 캐시를 사용해 네트워크 대역 등을 효율적으로 사용
- 조직 내에 특정 웹 사이트에 대한 액세스 제한
- 액세스 로그를 획득하는 정책을 지키려는 목적

**프록시 서버 사용 방법 2가지**

1. 캐시 사용 여부로 구분
2. 메시지 변경 여부로 구분

### 캐싱 프록시 (Cashing Proxy)

- 리스폰스를 중계할 때 프록시 서버 상에 **리소스 캐시를 보존해 두는** 타입의 프록시
  - 프록시로 같은 리소스에 리퀘스트가 오면, 오리진 서버에서 리소스를 획득하지 않고 캐시를 리스폰스로 되돌려주는 것

### 투명 프록시 (Transparent Proxy)

- 리퀘스트와 리스폰스를 중계를 할 때 **메시지 변경을 하지 않는** 타입의 프록시

### 비투과 프록시

- 리퀘스트와 리스폰스를 중계를 할 때 **메시지 변경하는** 타입의 프록시

## 5.2.2 게이트웨이

- 그 다음에 있는 서버가 **HTTP 서버 이외의 서비스를 제공하는 서버**
- 클라와 게이트웨이 사이를 암호화로 안전(secure)하게 접속함으로써 통신의 안정성을 높임
  - ex) 게이트웨이는 데이터베이스에 접속해 SQL 쿼리로 데이터를 얻는 곳에 이용
  - 쇼핑 사이트 등에서 신용 카드 결제 시스템 연계할 때 사용

## 5.2.3 터널

- 요구에 따라서 다른 서버와의 통신 경로를 확립
  - ex) 클라는 SSL 암호화 통신을 통해 서버와 안전하게 통신할 때 사용
- HTTP 리퀘스트를 해석하지 않고 다음 서버에 중계하는 역할
- 터널은 통신하고 있는 양쪽 끝의 접속이 끊어질 때에 종료됨

# 5-3. 리소스를 보관하는 캐시

- **캐시(Cache)** : 프록시 서버와 클라의 로컬 디스크에 보관된 **리소스의 사본**을 말함
- 캐시를 사용하면 오리진 서버까지 액세스할 필요가 없어 **통신량과 통신 시간을 절약함**
- 캐시 서버는 프록시 서버의 하나로 **캐싱 프록시**로 분류됨

**캐시 서버의 장점**

- 캐시를 이용하여 같은 데이터를 오리진 서버에 전송할 필요가 없음
  - 클라는 네트워크에 가까운 서버로 부터 리소스를 얻음
  - 서버는 같은 리퀘스트를 매번 처리하지 않아도 됨

## 5.3.1 캐시는 유효기간이 있다

- 캐시를 가지고 있더라도 클라의 요구나 캐시의 유효 기간 등에 의해서 오리진 서버에 리소스의 유효성을 확인 하거나 새로운 리소스를 다시 획득하러 감

## 5.3.2 클라이언트 측에도 캐시가 있다

- 캐시 서버뿐만 아니라 클라가 사용하는 **브라우저도 캐시를 가짐**
- 브라우저가 유효한 캐시를 가지고 있으면 같은 리소스의 액세스는 서버에 가지 않고 로컬 디스크로부터 불러옴
- 캐시 서버와 마찬가지로 리소스 유효 기간에 의해 오리진 서버에 리소스의 유효성을 확인 하거나 새로운 리소스를 다시 획득하러 감

# reference

> [그림으로 배우는 HTTP & Network Basic](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=51908132)