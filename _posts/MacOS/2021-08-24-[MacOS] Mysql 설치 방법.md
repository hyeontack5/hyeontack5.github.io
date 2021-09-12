---
title: "[MacOS] Mysql 설치 방법"
excerpt: "<!--more-->"
categories:
  - MacOS
tags:
  - MacOS
  - homebrew
  - mysql
toc: true
toc_sticky: true
toc_label: "[MacOS] Mysql 설치 방법"
toc_icon: "bookmark"
---

# homebrew로 MySQL 패키지 설치 방법

## MySQL 패키지 검색

```zsh
> brew search mysql
==> Formulae
automysqlbackup               mysql-client                  mysql-sandbox                 mysql@5.7
mysql                         mysql-client@5.7              mysql-search-replace          mysqltuner
mysql++                       mysql-connector-c++           mysql@5.6                     qt-mysql
==> Casks
mysql-connector-python                  mysql-utilities                         navicat-for-mysql
mysql-shell                             mysqlworkbench ✔                        sqlpro-for-mysql
```

## MySQL 설치 방법

- `brew install mysql` : 최신 mysql 패키지를 다운받을 수 있습니다.
- `brew install mysql@5.7` : mysql 5.7버전 패키지를 다운받을 수 있습니다.

> mysql@버전 : 원하는 버전을 선택하여 다운받을 수 있습니다.

**mysql@5.7을 설치하였습니다.**

## MySQL 설치 확인 방법

- `brew list`를 통해 설치된 항목을 조회할 수 있습니다.

```zsh
> brew list
mysql@5.7
```

## MySQL 삭제 방법

- `brew remove mysql@5.7`

`brew list`를 통해 삭제되었는지 확인이 가능합니다.

# MySQL 설정 방법

## 환경 변수 추가

- bash shell이 아닌 zsh shell을 기준으로 작성하였습니다

```zsh
> echo 'export PATH="/usr/local/opt/mysql@5.7/bin:$PATH"' >> ~/.zshrc
```

## 환경 변수 적용

```zsh
> source ~/.zshrc
```

## MySQL 서버 실행/중지

`mysql.server start` 명령어로 MySQL **서버를 실행**시킵니다.

```zsh
> mysql.server start
Starting MySQL
 SUCCESS!
```

`mysql.server stop` 명령어로 MySQL **서버를 중지**시킬 수 있습니다.

## MySQL 설정

MySQL 설정을 하기 위해서는 `mysql_secure_installation` 명령어를 입력합니다.

```zsh
mysql_secure_installation

Securing the MySQL server deployment.

Connecting to MySQL using a blank password.

VALIDATE PASSWORD PLUGIN can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD plugin?

Press y|Y for Yes, any other key for No:
```

## 비밀번호 유형 선택

비밀번호 가이드 설정에 대한 질문입니다.

- `Yes` : 복잡한 비밀번호 설정
- `No` : 쉬운 비밀번호 설정

```zsh
VALIDATE PASSWORD COMPONENT can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD component?

Press y|Y for Yes, any other key for No: No
```

**`No`를 선택했습니다.**

## 비밀번호 설정

사용할 새로운 비밀번호를 입력합니다.

```zsh
Please set the password for root here.

New password:

Re-enter new password:
```

**비밀번호는 간단하게 `mysql`로 했습니다.**

## 사용자 설정

Remove anonymous users? (Press y|Y for Yes. any other key for No) 
<br>사용자 설정을 하는 부분입니다.

- `Yes` : 접속하는 경우 `mysql -u root`처럼 **-u 옵션 필요**
- `No` : 접속하는 경우 `mysql`처럼 **-u 옵션 불필요**

```zsh
By default, a MySQL installation has an anonymous user,
allowing anyone to log into MySQL without having to have
a user account created for them. This is intended only for
testing, and to make the installation go a bit smoother.
You should remove them before moving into a production
environment.

Remove anonymous users? (Press y|Y for Yes, any other key for No) : Yes
```

**`Yes`를 선택했습니다.**

## 원격 접속 설정

Disallow root login remotely? (Press y|Y for Yes, any other key for No)
<br>다른 IP에서 root 아이디로 원격접속을 허용하는지에 대한 설정입니다.

- `Yes` : 원격접속 **불가능**
- `No` : 원격접속 **가능**

```zsh
Normally, root should only be allowed to connect from
'localhost'. This ensures that someone cannot guess at
the root password from the network.

Disallow root login remotely? (Press y|Y for Yes, any other key for No) : No
```

**`Yes`를 선택했습니다.**

## TEST 데이터베이스 설정

Remove test database and access to it? (Press y|Y for Yes, any other key for No)
<br>Test 데이터베이스를 설정하는 질문입니다

- `Yes` : Test 데이터베이스 **제거**
- `No` : Test 데이터베이스 **유지**

```zsh
By default, MySQL comes with a database named 'test' that
anyone can access. This is also intended only for testing,
and should be removed before moving into a production
environment.

Remove test database and access to it? (Press y|Y for Yes, any other key for No) : Yes
```

**`Yes`를 선택했습니다.**

## 변경된 권한을 테이블에 적용하는 설정

Reload privilege tables now? (Press y|Y for Yes, any other key for No)
<br>변경된 권한을 테이블에 적용하는 설정에 대한 질문입니다.

- `Yes` : 적용 시킨다
- `No` : 적용시키지 않는다

```zsh
Reloading the privilege tables will ensure that all changes
made so far will take effect immediately.

Reload privilege tables now? (Press y|Y for Yes, any other key for No) : Yes
```

**`Yes`를 선택했습니다.**

## 설정 완료

- **All done!**이 뜨면 모든 설정이 끝입니다.

<img src="/images/macos/mysql-setting.png" width="600" height="500"/>

# MySQL DB 로그인/로그아웃

`mysql -uroot -p` 명령어를 입력후 위에서 설정한 비밀번호를 입력후 로그인합니다.

```zsh
> mysql -uroot -p
Enter password:
```

- 정상적으로 로그인이 되면 **mysql>** 나옵니다.

```zsh
> mysql -uroot -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.7.35 Homebrew

Copyright (c) 2000, 2021, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

mysql> 쉘에서 **`exit` or `quit`** 명령어로 로그아웃할 수 있습니다.

```zsh
mysql> exit or quit
Bye
```

# MySQL 실행 절차

1. MySQL 서버 시작 : `mysql.server start`
2. MySQL DB 로그인 : `mysql -uroot -p`
3. MySQL DB 로그아웃 : `exit 또는 quit`
4. MySQL 서버 종료 : `mysql.server stop`

# reference

> [macOS MySQL 설치 및 설정 사용법](https://velog.io/@inyong_pang/MySQL-%EC%84%A4%EC%B9%98%EC%99%80-%EC%B4%88%EA%B8%B0-%EC%84%A4%EC%A0%95)
<br>[MySQL 설치와 초기 설정 for macOS](https://whitepaek.tistory.com/16)
<br>[MacOS brew로 mysql5.7 설치](https://saranf-click.tistory.com/24)
<br>[mysql5.7 버전 homebrew 로 설치](https://cishome.tistory.com/170)