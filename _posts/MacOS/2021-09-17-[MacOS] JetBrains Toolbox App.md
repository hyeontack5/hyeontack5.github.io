---
title: "[MacOS] JetBrains Toolbox App"
excerpt: "<!--more-->"
categories:
  - MacOS
tags:
  - MacOS
  - homebrew
  - toolbox
toc: true
toc_sticky: true
toc_label: "[MacOS] JetBrains Toolbox App"
toc_icon: "bookmark"
---

# homebrew로 Toolbox 설치방법

## Toolbox 란

- jetbrains사의 제품 전체를 관리해 주는 데스크톱 앱
- 모든 제품군의 버전 관리와 JVM 옵션 등을 조정 가능
  - 안드로이드 스튜디오, 웹스톰, 인텔리제이 커뮤니티/얼티메이트 등

## Toolbox 설치

`brew install jetbrains-toolbox`명령어를 입력하여 toolbox를 설치합니다.

```zsh
> brew install jetbrains-toolbox
Updating Homebrew...
==> Auto-updated Homebrew!
Updated 4 taps (homebrew/core, homebrew/cask, homebrew/cask-fonts and homebrew/services).
==> New Formulae
apache-pulsar    bat-extras       jpdfbookmarks    librist          pkgconf          red-tldr         viu
==> Updated Formulae
Updated 322 formulae.
==> New Casks
gcs                                                          remix-ide
==> Updated Casks
Updated 147 casks.

==> Downloading https://download.jetbrains.com/toolbox/jetbrains-toolbox-1.21.9712.dmg
==> Downloading from https://download-cdn.jetbrains.com/toolbox/jetbrains-toolbox-1.21.9712.dmg
######################################################################## 100.0%
==> Installing Cask jetbrains-toolbox
==> Moving App 'JetBrains Toolbox.app' to '/Applications/JetBrains Toolbox.app'
🍺  jetbrains-toolbox was successfully installed!
```

`jetbrains-toolbox was successfully installed!`가 뜨면 설치가 완료된 것입니다.

## 메모리 설정

설치된 Toolbox를 실행해서 **intellij를 설치** 합니다.

[Settings > Configuration > Maximum heap size]로 이동

<img src="/images/macos/intellij-settings.png" width="500" height="300"/>
<img src="/images/macos/intellij-memory-setting.png" width="500" height="300"/>

- **Maximum Heap Size**의 기본값은 750MB
  - intellij를 실행하는데, 어느 정도 메모리를 할당할지 결정하는 값
- 기본값은 개발 PC의 메모리가 4GB이하일 때를 가정하고 설정된 값
- 개발 PC의 메모리 **8GB -> 1024~2048** / **16GB -> 2048~4096**로 설정

16GB 메모리를 사용하고 있기 때문에 최소인 2048로 설정했습니다.

# reference

> [스프링 부트와 AWS로 혼자 구현하는 웹 서비스](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=218568947)
<br>[IntelliJ IDEA 프로젝트에 활용하기](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=243441458)
<br>[Toolbox App](https://www.jetbrains.com/ko-kr/toolbox-app/)
<br>[Homebrew Formulae](https://formulae.brew.sh/cask/jetbrains-toolbox)