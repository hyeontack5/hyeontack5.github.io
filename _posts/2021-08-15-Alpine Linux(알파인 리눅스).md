---
title: "[Linux] Alpine(알파인)"
excerpt: "<!--more-->"
categories:
  - Linux
tags:
  - Linux
  - Docker
toc: true
toc_sticky: true
toc_label: "[Linux] Alpine(알파인)"
toc_icon: "bookmark"
---

# Alpine Linux(알파인 리눅스) 란?

알파인 리눅스는 가볍고 간단하며, 보안성을 목적으로 개발한 리눅스 배포판입니다.

alpine linux는 CentOS 나 Ubuntu와 다르게 Main OS 로 사용하지 않고, 용량이 80M인 초경량화된 배포판이므로 Embbeded(임베디드), 네트웍 서버 등 특정 용도에 적합하며 **도커 컨테이너의 OS**로 많이 사용합니다.

용량을 줄이기 위해 시스템의 기본 C runtime을 glibc 대신 musl libc를 사용하며 다양한 쉘 명령어는 GNU util 대신 **busybox**를 탑재하였습니다.

# BusyBox 란?

BusyBox는 쉽게 말해 조그만 상자안에 standard utilities(작은 응용프로그램)들을 담아 놓은 것이라고 생각하면 됩니다.

BusyBox란 일종의 명령어 모음집? 압축파일?이라고 보면 될거 같습니다.
리눅스에서 사용되는 각 명령어들만 모아 놓아도 굉장히 클텐데, BusyBox에서는 각각에 함수들을 최소 사이즈로 다시 구현하였습니다. 그렇기 때문에 Embbeded(임베디드), 네트웍 서버 등 특정 용도에 적합하며 도커 컨테이너의 OS로 많이 사용합니다.

# APK 패키지 관리자

알파인 리눅스에서는 APK를 package management(패키지 관리자)로 사용합니다.

# APK 간단한 명령어

|명령|설명|
|---|---|
|apk update|패키지 저장소 목록을 업데이트|
|apk upgrade|패키지 저|
|apk search <패키지>|패키지 저장소 목록에서 패키지를 검색|
|apk add <패키지[=버전]>|특정 패키지를 설치, 뒤에 >나 = 등을 붙여 버전 정보를 추가로 작성할 수 있다|
|apk del <패키지>|특정 패키지를 제거|
|apk info|설치된 모든 패키지를 나열|

# reference
> [Alpine Linux - 나무위키](https://namu.wiki/w/Alpine%20Linux)