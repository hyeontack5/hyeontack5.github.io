---
title: "[EC2 ubuntu:20.04LTS] vscode에 ssh연결방법"
excerpt: "<!--more-->"
categories:
  - AWS
tags:
  - vscode
  - aws
toc: true
toc_sticky: true
toc_label: "vscode에 ssh연결방법"
toc_icon: "bookmark"
---

# AWS의 인스턴스 접속

[EC2 > 인스턴스 > 접속할 인스턴스]로 이동 후, 연결 버튼을 눌러줍니다.

![vscode에 ssh연결방법_1](/images/vscode에 ssh연결방법_1.png)

---

[SSH 클라이언트]을 눌러줍니다.

인스턴스를 생성할 때 만든 pem 키를 ~/.ssh에 저장 후 `cd ~/.ssh`로 이동하여 터미널에

1. chmod 400 ...로 시작하는 내용을 복사하여 터미널에 입력하면 pem 권한을 변경 해줍니다.
2. ssh -i ...로 시작하는 내용을 복사하여 터미널에 입력해줍니다.

그러면 터미널에서 EC2 인스턴스에 접근을 할 수 있는 것을 확인할 수 있습니다.

![vscode에 ssh연결방법_2](/images/vscode에 ssh연결방법_2.png)