---
title: "[EC2 ubuntu:20.04LTS] vscode에 ssh연결방법"
excerpt: "<!--more-->"
categories:
  - AWS
tags:
  - aws
  - vscode
toc: true
toc_sticky: true
toc_label: "vscode에 ssh연결방법"
toc_icon: "bookmark"
---

# 터미널로 AWS의 인스턴스 접속 방법

[EC2 > 인스턴스 > 접속할 인스턴스]로 이동 후, 연결 버튼을 눌러줍니다.

![vscode에 ssh연결방법_1](/images/vscode에 ssh연결방법_1.png)

[SSH 클라이언트]을 눌러줍니다.
<br>인스턴스를 생성할 때 만든 pem 키를 `~/.ssh`에 저장 후 `cd ~/.ssh`로 이동하여 터미널에

1. `chmod 400 ...`로 시작하는 내용을 복사하여 터미널에 입력하면 pem 권한을 변경 해줍니다.
2. `ssh -i ...`로 시작하는 내용을 복사하여 터미널에 입력해줍니다.

그러면 터미널에서 EC2 인스턴스에 접근을 할 수 있는 것을 확인할 수 있습니다.

![vscode에 ssh연결방법_2](/images/vscode에 ssh연결방법_2.png)

# vscode로 AWS의 인스턴스 접속 방법

## Extension에서 확장프로그램 설치

Extension에서 `remote ssh`를 검색해서 
<br>`Remote - SSH`와 `Remote - SSH: Editing Configuration Files`을 설치합니다.

![vscode에 ssh연결방법_4](/images/vscode에 ssh연결방법_4.png)

![vscode에 ssh연결방법_5](/images/vscode에 ssh연결방법_5.png)

## vscode에서 설정

위와 같은 방법으로 `cd ~/.ssh`로 .pem키가 저장된 위치로 이동하여 터미널에

1. `chmod 400 ...`로 시작하는 내용을 복사하여 터미널에 입력하면 pem 권한을 변경 해줍니다.
2. `ec2-...ap-northeast-2.compute.amazonaws.com`을 복사합니다.

![vscode에 ssh연결방법_3](/images/vscode에 ssh연결방법_3.png)

`fn + F1` or `cmd + shift + p`을 눌러 커맨드창에 `configuration`을 입력해 
<br>`Remote-SSH: Open Configuration File...`를 선택합니다. 

![vscode에 ssh연결방법_6](/images/vscode에 ssh연결방법_6.png)

![vscode에 ssh연결방법_7](/images/vscode에 ssh연결방법_7.png)

![vscode에 ssh연결방법_8](/images/vscode에 ssh연결방법_8.png)

* Host : ssh 접속시 표시될 이름입니다. 아무거나 적어도 됩니다. 저는 그냥 .pem의 이름과 같은걸 사용합니다.
ex) key.pem -> key 라고 적습니다.
* HostName : AWS에서 제공해주는 퍼블릭DNS 주소를 적습니다.
<br>위에서 복사한 `ec2-...ap-northeast-2.compute.amazonaws.com`를 붙여넣으면 됩니다.
* User : `ubuntu`처럼 AWS에서 정해준 서버의 유저 이름을 적습니다.
<br>위에 `ssh -i...`로 시작하는 내용에 보면 @ 앞에 User를 확인할 수 있습니다.
* IdentityFile : .pem 키가 저장된 경로와 파일명을 적습니다.

이제 다시 `fn + F1` or `cmd + shift + p`을 눌러 `Remote-SSH: Connect to Host...`를 선택합니다. 

![vscode에 ssh연결방법_9](/images/vscode에 ssh연결방법_9.png)

그러면 위에서 저장한 Host 대로 key가 등록되어 있습니다. 
<br>선택하면 .pem 키를 통해 vscode에서 EC2 인스턴스에 접근을 할 수 있는 것을 확인할 수 있습니다.

![vscode에 ssh연결방법_10](/images/vscode에 ssh연결방법_10.png)

# reference

> [Remote Development with Visual Studio Code on Amazon EC2](https://letswp.io/remote-development-visual-studio-code-amazon-ec2/)
<br>[VS code Remote-ssh로 AWS EC2 인스턴스 접속 및 개발하는 법](https://director-joe.kr/80)
<br>[Remote 원격 아마존 AWS SSH 클라이언트 접속](https://tttap.tistory.com/141)
<br>[Vscode SSH 로 AWS 바로 접속하기](https://velog.io/@ant-now/Vscode-SSH-%EB%A1%9C-AWS-%EB%B0%94%EB%A1%9C-%EC%A0%91%EC%86%8D%ED%95%98%EA%B8%B0)