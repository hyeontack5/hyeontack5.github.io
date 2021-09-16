---
title: "[MacOS] JAVA 설치 방법"
excerpt: "<!--more-->"
categories:
  - MacOS
tags:
  - MacOS
  - homebrew
  - java
toc: true
toc_sticky: true
toc_label: "[MacOS] JAVA 설치 방법"
toc_icon: "bookmark"
---

# homebrew로 JDK 설치 방법

## JDK 란

- **JDK(Java Development Kit)** : 자바 코드의 번역과 실행을 담당하는 **자바 개발 도구**
- JDK는 JRE 기능을 포함하고 있으며, 자바프로그램이 JVM에 의해 실행할 수 있도록 해줍니다.
- JDK를 설치하면 **JVM**(**Hotspot**이라고도 표현, Java 기술의 핵심)도 함께 설치됩니다.

<img src="/images/macos/jdk.png" width="600" height="600"/>

## Oracle JDK와 OpenJDK

- 오라클이 썬을 인수하면서, **오라클의 Oracle JDK**와 **썬의 OpenJDK**로 나뉘어 졌습니다.
- JDK는 1.8 이상부터 유료로 변경되었기에, 사용하기 위해서는 라이센스 비용을 지불해야 합니다.
물론 비상업적(개인PC 등)인 경우에는 무료로 사용이 가능합니다.
- 유료로 전환된 Oracle JDK 대신 무료로 사용할 수 있는게 **OpenJDK** 입니다.

Oracle JDK는 오라클에서 추가적으로 제공하는 기능 이외에는 OpenJDK와 별차이 없습니다.

> Oracle JDK = 상업용, 사용 목적에 따라 무료 or 유료
<br>OpenJDK = 개발용, 오픈소스 기반으로 무료!

## AdoptOpenJDK 란

- AdoptOpenJDK는 사전에 prebuild 형태로 java binary를 무료로 제공하는 커뮤니티 그룹
- AdoptOpenJDK는 8, 11 버전에 대해 LTS 지원을 보장하고 있습니다.

# AdoptOpenJDK 설치

## 기존 Java 설치 여부 확인

명령어로 자바가 설치되어 있는지 확인합니다.

```zsh
> java --version
```

자바를 처음 설치하는 경우라면 없겠죠?

## OpenJDK 저장소 연결

인터넷 어딘가에 저장되어 있는 OpenJDK 저장소 위치를 연결해줍니다.

```zsh
> brew tap AdoptOpenJDK/openjdk
```

## 설치할 자바 버전 고르기

가장 많이 사용되고 있는 **Java 8** 버전을 설치하겠습니다.

<img src="/images/macos/openjdk-version.png" width="600" height="600"/>

## OpenJDK 검색

`brew search openjdk8`명령어를 입력하여 설치하려는 패키지 있는지 확인합니다.

```zsh
> brew search openjdk8
==> Formulae
openjdk@8                                            openjdk                                              openjdk@11
==> Casks
adoptopenjdk8                                        adoptopenjdk8-openj9                                 adoptopenjdk8-openj9-jre-large
adoptopenjdk8-jre                                    adoptopenjdk8-openj9-jre                             adoptopenjdk8-openj9-large
```

## OpenJDK 설치

`brew install adoptopenjdk8`명령어를 입력하여 **Java 8** 버전을 설치 합니다.

```zsh
> brew install adoptopenjdk8
==> Downloading https://github.com/AdoptOpenJDK/openjdk8-binaries/releases/download/jdk8u292-b10/OpenJDK8U-jdk_x64_mac_hotspot_8u292b10.pkg
==> Downloading from https://github-releases.githubusercontent.com/140418865/bbad4180-a2e0-11eb-8274-f16f6a90729c?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20210913%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20210913T095720Z&X-Amz-Expires=300&X-Amz-Signat
######################################################################## 100.0%
==> Installing Cask adoptopenjdk8
==> Running installer for adoptopenjdk8; your password may be necessary.
Package installers may write to any location; options such as `--appdir` are ignored.
Password:
installer: Package name is AdoptOpenJDK
installer: Installing at base path /
installer: The install was successful.
package-id: net.adoptopenjdk.8.jdk
version: 1.8.0_292-b10
volume: /
location:
install-time: 1631527239
🍺  adoptopenjdk8 was successfully installed!
```

`adoptopenjdk8 was successfully installed!`가 뜨면 설치가 완료된 것입니다.

## 설치 확인

```zsh
> java -version
openjdk version "1.8.0_292"
OpenJDK Runtime Environment (AdoptOpenJDK)(build 1.8.0_292-b10)
OpenJDK 64-Bit Server VM (AdoptOpenJDK)(build 25.292-b10, mixed mode)
```

# reference

> [맥에서 Brew로 자바 설치하기(feat. 자바버전 바꾸기)](https://llighter.github.io/install-java-on-mac/)
<br>[How to install Java JDK on macOS](https://mkyong.com/java/how-to-install-java-on-mac-osx/)
<br>[homebrew로 openjdk 설치하기](https://findstar.pe.kr/2019/01/20/install-openjdk-by-homebrew/)
<br>[Mac에서 Open JDK 설치하기](https://timevoyage.tistory.com/145)
<br>[[JAVA] OpenJDK 다운로드 및 설치하기 (JDK 다운 및 설치하기, JDK 란, 환경변수 잡는법)](https://mozi.tistory.com/428)
<br>[Java 유료 논쟁, Oracle JDK와 OpenJDK의 차이 정리](https://jsonobject.tistory.com/395)