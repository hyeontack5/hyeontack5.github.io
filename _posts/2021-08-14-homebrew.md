---
title: "[MacOS] homebrew"
excerpt: "<!--more-->"
categories:
  - MacOS
tags:
  - homebrew
  - MacOS
toc: true
toc_sticky: true
toc_label: "[MacOS] homebrew"
toc_icon: "bookmark"
---

# homebrew 란?

MacOS용 package management(패키지 관리자)입니다.
terminal(터미널)에서 명령어를 통해 자신이 필요한 프로그램(모듈)을 설치, 삭제, 업데이트를 손쉽게 관리할 수 있습니다.

개발에 대한 경험이 있으면

``` 
Ubuntu(우분투) : apt-get install

CentOS(센트OS) : yum install

MacOS(맥) : brew insatll
```

을 이용하여 필요한 프로그램(모듈)을 설치할 수 있습니다.

# homebrew(홈브류)를 왜 사용해야될까?

Mac 유저라면, 자신에게 맞는 프로그램들을 설치하게 됩니다.

프로그램을 사용하려면 보통 App Store 또는 해당 사이트에 접속해서 프로그램을 다운로드하는게 일반적인 방법입니다. 하지만 이런 경우 원치 않는 프로그램이 자신도 모르게 설치될 수도 있고 나중에 프로그램을 재설치, 삭제, 업데이트할 때 기존의 데이터가 남아있는 경우가 많습니다.

"**Homebrew**"를 사용할 경우 이런 문제없이 손쉽고 깔끔하게 프로그램을 설치, 삭제, 업데이트할 수 있는 강력한 MacOS 용 패키지 관리자입니다.

그래서 프로그램 사용이 많은 개발자가 손쉽게 패키지를 관리하기 위해서 사용하는 도구 중 하나입니다.

# homebrew 설치방법

`command + space bar`를 클릭하여 terminal을 실행시키고, 아래 명령어를 복사 붙여넣기 하면 homebrew가 설치됩니다.

```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
[homebrew 공식사이트](https://brew.sh/index_ko)
# homebrew 종류

* homebrew : 개발 관련 패키지 설치

* cask : 웹사이트에서 받을 수 있는 어플리케이션 설치

* mas : 앱스토어에서 받을 수 있는 어플리케이션 설치

# homebrew 명령어

```
$ brew search [프로그램(모듈) 이름] : 설치가능한 프로그램(모듈) 찾기
$ brew install [프로그램(모듈) 이름] : 프로그램(모듈) 설치
$ brew list : brew로 설치된 프로그램(모듈) 조회
$ brew update : brew로 설치된 프로그램(모듈) 업데이트
$ brew uninstall [프로그램(모듈) 이름] : 프로그램(모듈) 삭제
$ brew remove [프로그램(모듈) 이름] : 프로그램(모듈) 완전삭제
```
