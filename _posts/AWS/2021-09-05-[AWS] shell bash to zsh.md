---
title: "[EC2 ubuntu:20.04LTS] shell bash -> zsh로 변경하기"
excerpt: "<!--more-->"
categories:
  - AWS
tags:
  - aws
  - vscode
toc: true
toc_sticky: true
toc_label: "shell bash -> zsh로 변경하기"
toc_icon: "bookmark"
---

# install zsh

먼저 apt를 사용하기 전 패키지 업데이트는 필수입니다.

```bash
$ sudo apt update
```

위 명령어를 완료 한 다음 zsh를 설치 합니다.

```bash
$ sudo apt install -y zsh
```

설치가 완료 되었다면 zsh의 경로를 확인합니다.

```bash
$ which zsh
# /usr/bin/zsh
```

# 기본 쉘 변경

먼저 passwd 파일을 vim으로 엽니다.

```bash
$ sudo vim /etc/passwd
```

그리고 하단으로 내려가면

![bash to zsh](/images/bash to zsh_1.png)

기본 쉘이 사용자 이름으로 설정되어 있는 것을 볼 수 있습니다. 
<br>i를 눌러 입력모드로 아까전에 확인 하였던 zsh경로로 수정합니다. 
<br>전체 경로를 다 써도 상관은 없습니다.

![bash to zsh](/images/bash to zsh_2.png)

수정 하였다면 `esc`를 눌러 입력모드를 빠져나오고 
<br>`:wq`를 누르고 `enter`를 누르면 저장 후 종료됩니다.

ec2 인스턴스를 재부팅 해줘야 zsh이 적용됩니다

```bash
$ echo $SHELL
# /bin/zsh
```

![bash to zsh](/images/bash to zsh_3.png)

위 명령어를 통해서 결과가 `/bin/zsh`가 나오는지 확인합니다