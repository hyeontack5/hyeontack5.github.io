---
title: "[MacOS] vscode Vim 플러그인 연속 키 입력 안되는 문제"
excerpt: "<!--more-->"
categories:
  - MacO제
tags:
  - MacOS
  - vscode
toc: true
toc_sticky: true
toc_label: "[MacOS] vscode Vim 플러그인 연속 키 입력 안되는 문제 해결 방법"
toc_icon: "bookmark"
---

# vscdoe Vim 플러그인

- 커맨드 모드에서 빠르게 hjkl키로 소스코드 사이를 움직을 수 있는데 vscode에서 vim을 설치한 후 키를 계속 누르고 있으면 입력이 연속으로 되지 않는 현상이 발생했습니다.

- 스택 오버플로우를 확인해보니 아래와 같은 명령어로 해결할 수 있다고 하여 문제를 해결했습니다.

- 터미널 창에 아래와 같이 입력 후 엔터

```zsh
> defaults write com.microsoft.VSCode ApplePressAndHoldEnabled -bool false
```

- 그 후 vscode를 종료하고 다시 실행시킵니다. 그러면 아무 문제 없이 vim 모드에서 hjkl 키를 반복해서 누를 필요없이 연속 입력이 가능해집니다.

# Reference
