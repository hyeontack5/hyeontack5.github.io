---
title: "[EC2 ubuntu:20.04LTS] oh-my-zsh 설치"
excerpt: "<!--more-->"
categories:
  - AWS
tags:
  - aws
toc: true
toc_sticky: true
toc_label: "oh-my-zsh 설치"
toc_icon: "bookmark"
---

# install oh-my-zsh

추가적인 확장 기능을 이용하고 싶으면 oh-my-zsh 설치를 권장합니다.

```bash
$ sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

위의 명령을 입력 결과

<img src="/images/oh-my-zsh-install.png" width="600" height="300"/>

# Agnoster 테마 적용하기

아래의 명령어를 입력하여 `.zshrc`파일을 수정하여 줍니다.

```bash
$ vi ~/.zshrc
```

아래의 이미지와 같이 `ZSH-THEME`부분을 **agnoster**로 변경해 줍니다.

<img src="/images/agnoster-before.png" width="600" height="300"/>

<img src="/images/agnoster-after.png" width="600" height="300"/>

아래 명령어를 입력하여 수정된 내용으로 실행되게 합니다.

```bash
$ source ~/.zshrc
```

# Agnoster 적용 모습

<img src="/images/oh-my-zsh-installed.png" width="600" height="300"/>