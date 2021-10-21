---
title: "[Network] HTTP 헤더"
excerpt: "<!--more-->"
categories:
  - Network
tags:
  - Network
  - 그림으로 배우는 HTTP & Network Basic
toc: true
toc_sticky: true
toc_label: "[Network] HTTP 헤더"
toc_icon: "bookmark"
---

# 6-1. HTTP 메시지 헤더

- HTTP 프로토콜의 리퀘스트와 리스폰스에는 **반드시 메시지 헤더가 포함**되어 있음
  - 메시지 헤더에는 클라와 서버가 리퀘스트나 리스폰스를 처리하기 위한 정보가 들어있음

**리퀘스트의 HTTP 메시지**

- 메소드, URI, HTTP 버전, HTTP 헤더 필드 등으로 구성

**리스폰스의 HTTP 메시지**

- HTTP 메시지와 HTTP 버전, 상태 코드(코드와 설명), HTTP 헤더 필드 등으로 구성

  - HTTP 헤더 필드 : 리퀘스트와 리스폰스 양쪽 모두 존재하는 HTTP 메시지에 관한 정보를 가짐

# 6-2. HTTP 헤더 필드

## HTTP 헤더 필드는 중요한 정보를 전달한다

**HTTP 헤더 필드**

- HTTP 메서지를 구성하는 요소의 하나
- 리퀘스트와 리스폰스에 사용
- 중요한 정보를 전달하는 역할
- 메시지 바디의 크기나 사용하고 있는 언어, 인증 정보 등을 브라우저 or 서버에 제공하기 위해 사용

## HTTP 헤더 필드의 구조

- 헤더 필드 명과 필드 값을 콜론(:)으로 구분하여 구성

```
헤더 필드 명 : 필드 값
```

- 예를들어 HTTP 헤드 필드에 메시지 바디의 오브젝트의 타입을 가리키는 `Content-Type`가 포함된 경우
  - 헤드 필드 명 : `Content-Type`
  - 필드 값 : 문자열 `text/html`

```
ex) Content-Type:text/html
```

- 하나의 HTTP 헤더 필드가 여러 개의 필드 값을 가질 수 있음

```
ex) Keep-Alive:timeout=15,max=100
```

**HTTP 헤더 필드가 중복된 경우는 어떻게 될까?**

- HTTP 메시지 헤더 중에 같은 헤더 필드 명이 두 개 이상 있다면?
  - 브라우저에 따라 다르게 동작함
  - 어떤 브라우저는 최초의 헤더 필드를 우선적으로 처리하고 어떤 브라우저는 마지막 헤더 필드를 우선적으로 처리함

## 4종류의 HTTP 헤더 필드

HTTP 헤더 필드는 용도에 따라 4종류로 분류

- **일반적인 헤더 필드 (General Header Fields)**
  - 리퀘스트 메시지와 리스폰스 메시지 둘 다 사용되는 헤더
- **리퀘스트 헤더 필드 (Request Header Fields)**
  - 클라에서 서버로 송신된 **리퀘스트 메시지에 사용되는 헤더**
  - 리퀘스트의 부가적 정보, 클라의 정보, 리스폰스의 콘텐츠에 관한 우선 순위 등을 부가함
- **리스폰스 헤더 필드 (Response Header Fields)**
  - 서버에서 클라로 송신한 **리스폰스 메시지에 사용되는 헤더**
  - 리스폰스의 정보, 서버의 정보, 클라의 추가 정보 요구 등을 부가함
- **엔티티 헤더 필드 (Entity Header Fileds)**
  - 리퀘스트 메시지와 리스폰스 메시지에 포함된 엔티티에 사용되는 헤더
  - 콘텐츠 갱신 시간 등의 엔티티에 고나한 정보를 부가함

## HTTP/1.1 헤더 필드 일람

- HTTP/1.1에 정의되어 있는 헤더 필드는 47종류가 있음

*일반 헤더 필드*

| 헤더 필드명       | 설명                              |
| ----------------- | --------------------------------- |
| Cache-Control     | 캐싱 동작 지정                    |
| Connection        | Hop-by-hop 헤더, 커넥션 관리      |
| Date              | 메시지 생성 날짜                  |
| Pragma            | 메시지 제어                       |
| Trailer           | 메시지의 끝에 있는 헤더의 일람    |
| Transfer-Encoding | 메시지 바디의 전송 코딩 형식 지정 |
| Upgrade           | 다른 프로토콜에 업그레이드        |
| Via               | 프록시 서버에 관한 정보           |
| Warning           | 에러 통지                         |

*리퀘스트 헤더 필드*

| 헤더 필드명         | 설명                                                         |
| ------------------- | ------------------------------------------------------------ |
| Accept              | 유저 에이전트가 처리 가능한 미디어 타입                      |
| Accept-Charset      | 문자셋 우선 순위                                             |
| Accept-Encoding     | 콘텐츠 인코딩 우선 순위                                      |
| Accpet-Language     | 언어(자연어) 우선 순위                                       |
| Authorization       | 웹 인증을 위한 정보                                          |
| Expect              | 서버에 대한 특정 동작의 기대                                 |
| From                | 유저의 메일 주소                                             |
| Host                | 요구된 리소스의 호스트                                       |
| If-Match            | 엔티티 태그의 비교                                           |
| If-Modified-Since   | 리소스의 갱신 시간 비교                                      |
| If-None-Match       | 엔티티 태그의 비교                                           |
| If-Range            | 리소스가 갱신되지 않은 경우에 엔티티의 바이트 범위의 요구를 송신 |
| If-Unmodified-Since | 리소스의 갱신 시간 비교(If-Modified-Since의 반대)            |
| Max-Forwards        | 최대 전송 홉 수                                              |
| Proxy-Authorization | 프록시 서버의 클라이언트 인증을 위한 정보                    |
| Range               | 엔티티 바이트 범위 요구                                      |
| Referer             | 리퀘스트중의 URI를 취득하는 곳                               |
| TE                  | 전송 인코딩의 우선 순위                                      |
| User-Agent          | HTTP 클라이언트의 정보                                       |

*리스폰스 헤더 필드*

| 헤더 필드명        | 설명                                              |
| ------------------ | ------------------------------------------------- |
| Accept-Ranges      | 바이트 단위의 요구를 수신할 수 있는지 없는지 여부 |
| Age                | 리소스의 저정 경과 시간                           |
| Etag               | 리소스 특정하기 위한 정보                         |
| Location           | 클라이언트를 지정한 URI에 리다이렉트              |
| Proxy-Authenticate | 프록시 서버의 클라이언트 인증을 위한 정보         |
| Retry-After        | 리퀘스트 재시행의 타이밍 요구                     |
| Server             | HTTP 서버 정보                                    |
| Vary               | 프록시 서버에 대한 캐시 관리 정보                 |
| WWW-Authenticate   | 서버의 클라이언트 인증을 위한 정보                |

*엔티티 헤더 필드*

| 헤더 필드명      | 설명                                 |
| ---------------- | ------------------------------------ |
| Allow            | 리소스가 제공하는 HTTP 메소드        |
| Content-Encoding | 엔티티 바디에 적용되는 콘텐츠 인코딩 |
| Content-Language | 엔티티의 자연어                      |
| Content-Length   | 엔티티 바디의 사이즈(단위:바이트)    |
| Content-Location | 리소스에 대응하는 대체 URI           |
| Content-MD5      | 엔티티 바디의 메시지 다이제스트      |
| Content-Range    | 엔티티 바디의 범위 위치              |
| Content-Type     | 엔티티 바디의 미디어 타입            |
| Expires          | 엔티티 바디의 유효기한 날짜          |
| Last-Modified    | 리소스의 최종 갱신 날짜              |

## HTTP/1.1 이외의 헤더 필드

- HTTP에서 교환되는 HTTP 헤더 필드가 47종류 이외에 더 있음
  - ex) 쿠기와 Set-Cookie, Content-Disposition 등

## End-to-end 헤더와 Hop-by-hop 헤더

- HTTP 헤더 필드는 캐시와 비캐시 프록시의 동작을 정의를 위해 2가지로 분류 되어 있음

**End-to-end 헤더**

- 헤더는 리퀘스트나 리스폰스의 최종 수신자에게 전송됨
- 캐시에서 구축된 리스폰스 중 보존되야 하고, 다시 전송되지 않으면 안되도록 되어 있음

**Hop-by-hop 헤더**

- 헤더는 한 번 전송에 대해서만 유효하고 캐시와 프록시에 의해서 전송되지 않는 것도 있음
- HTTP/1.1과 그 이후에서 사용되는 Hop-by-hop 헤더는 Connection 헤더 필드에 열거해야 함

**HTTP/1.1에서 Hop-by-hop 헤더에 8개의 헤더 필드**

- Connetion
- Keep-Alive
- Proxy-Authenticate
- Proxy-Authorization
- Trailer
- TE
- Transfer-Encoding
- Upgrade

이외에는 모두 End-by-end 헤더에 분류됨

# 6-3. HTTP/1.1 일반 헤더 필드

## Cache-Control

- **디렉티브**로 불리는 명령을 사용하여 캐싱 동작을 지정함
- 지정한 디렉티브에는 파라미터가 있는 것과 없는 것이 있음
  - 여러 개의 디렉티브를 지정하는 경우 콤마(,)로 구분
- 디렉티브는 리퀘스트 및 리스폰스 할 때에 사용할 수 있음

```
ex) Cache-Control: private, max-age=0, no-cache
```

**Cache-Control 디렉티브 일람**

*캐시 리퀘스트 디렉티브*

| 디렉티브           | 파라미터  | 설명                                                 |
| ------------------ | --------- | ---------------------------------------------------- |
| no-cache           | 없음      | 오리진 서버에 강제적인 재검증                        |
| no-store           | 없음      | 캐시는 리퀘스트, 리스폰스의 일부분을 보존해서는 안됨 |
| max-age = [초]     | 필수      | 리스폰스의 최대 age 값                               |
| max-state( = [초]) | 생략 가능 | 기한이 지난 리스폰스를 수신                          |

*캐시 리스폰스 디렉티브*

| 디렉티브        | 파라미터  | 설명                                                         |
| --------------- | --------- | ------------------------------------------------------------ |
| public          | 없음      | 어딘가에 리스폰스 캐시가 가능                                |
| private         | 생략 가능 | 특정 유저에 대해서만 리스폰스                                |
| no-cache        | 생략 가능 | 유효성의 재확인 없이는 캐시는 사용해서는 안됨                |
| no-store        | 없음      | 캐시는 리퀘스트,<br>리스폰스의 일부분을 보존해서는 안됨      |
| no-transform    | 없음      | 프록시는 미디어 타입을 변경해서는 안됨                       |
| must-revalidate | 없음      | 캐시 가능하지만 오리진 서버에 리소스의 재확인을 요구         |
| proxy-revaliate | 없음      | 중간 캐시 서버에 대해서 캐시했던 리스폰스의 유효성의 재확인을 요구 |
| max-age = [초]  | 필수      | 리스폰스의 최대 Age 값                                       |
| s-maxage = [초] | 필수      | 공유 캐시 서버의 리스폰스 최대 Age 값                        |
| cache-extension | -         | 새로운 디렉티브를 위한 토큰                                  |

**캐시가 가능한지 여부를 나타내는 디렉티브**

_1)_ **public 디렉티브**

```
Cache-Control: public
```

- 다른 유저에게도 돌려줄 수 있는 캐시를 해도 좋다는 것을 의미

_2)_ **private 디렉티브**

```
Cache-Control: private
```

- 리스폰스는 특정 유저만을 대상으로 하고 있다는 것을 의미
- `public` 디렉티브와 기능이 반대
- 캐시 서버는 특정 유저를 위해 리소스를 캐시할 수 있지만, 다른 유저로 부터 같은 리퀘스트가 온다면 그 캐시를 반환하지 않도록 함

_3)_ **no-cache 디렉티브**

```
Cache-Control: no-cache
```

- 캐시로부터 오래된 리소스가 반환되는것을 막기 위해 사용
- **클라의 리퀘스트**로 `no-cache` 디렉티브 사용된 경우
  - 캐시된 리스폰스를 받지 않고 중간 캐시 서버가 오리진 서버까지 리퀘스트를 전송함
- **서버의 리스폰스**에 `no-cache` 디렉티브 사용된 경우
  - 캐시 서버는 리소스를 저장할 수 없음
  - 오리진 서버는 캐시 서버가 리소스 유효성의 재확인 없이는 그 리스폰스 사용하지 못하게 함

```
Cache-Control: no-cache=Location
```

- `no-cache`의 필드 값에 헤더 필드 명으로 지정된 헤더 필드만 캐시할 수 없음
  - 지정된 헤더 필드 이외에는 캐시 가능

**캐시로 보존 가능한 것을 제어하는 디렉티브**

_1)_ **no-store 디렉티브**

```
Cache-Control: no-store
```

- 리퀘스트(대응되는 리스폰스) 혹은 리스폰스에 기밀 정보가 포함되어 있음을 나타냄
- 캐시는 리퀘스트, 리스폰스의 일부분을 로컬 스토리지에 보존하지 못하게 지정함

**캐시 기한이나 검증을 지정하는 디렉티브**

_1)_ **s-maxage 디렉티브**

```
Cache-Control: s-maxage=604800(단위: 초)
```

- `s-maxage` 디렉티브의 기능은 `max-age` 디렉티브와 동일함
- 다른 점은 여러 유저가 이용할 수 있는 공유 캐시 서버에만 적용되는 것
  - 같은 유저에 반복해서 리스폰스를 반환하는 캐시 서버는 무효한 디렉티브
- `s-maxage` 디렉티브가 사용되는 경우, Expires 헤더 필드와 `max-age` 디렉티브는 무시됨

_2)_ **max-age 디렉티브**

```
Cache-Control: max-age=604800(단위: 초)
```

- 클라의 리퀘스트로 `max-age` 디렉티브가 사용되면 지정되었던 값보다 새로운 경우에는 캐시되었던 리소스를 받아들일 수 있음
- 지정한 값이 0이면 캐시 서버는 리퀘스트를 항상 오리진 서버에 넘길 필요 있음
- 서버의 리스폰스에서 `max-age` 디렉티브가 사용되는 경우, 캐시 서버가 유효성의 재확인을 하지 않고 리소스를 캐시에 보존해 두는 최대 시간을 나타냄
- HTTP/1.1 캐시 서버는 동시에 Expires 헤더 필드가 달린 경우에는 `max-age` 디렉티브의 지정을 우선하고 Expires 헤더 필드를 무시함
  - HTTP/1.0 캐시 서버는 반대로 `max-age` 디렉티브가 무시됨

_3)_ **min-fresh 디렉티브**

```
Cache-Control: min-fresh=60 (단위: 초)
```

- 캐시된 리소스가 적어도 지정된 시간은 최신 상태의 것을 반환하도록 캐시 서버에 요구함
  - ex) 60초로 지정되어 있는 경우 60초 이내에 유효 기한이 끝나는 리소스를 리스폰스로 반환하면 안됨

_1)_ **max-stale 디렉티브**

```
Cache-Control: max-stale=3600 (단위: 초)
```

- 캐시된 리소스의 유효 기간이 끝났더라도 받아들일 수 있음을 나타냄
- 디렉티브에 **값이 지정되어 있지 않는 경우**, 클라는 아무리 시간이 경과했더라도 리스폰스를 받아들임
- **값이 지정되어 있는 경우**, 유효 기한이 지난 후로부터 지정 시간 내라면 받아들인다는 뜻을 서버에 전달함

_2)_ **only-if-cached 디렉티브**

```
Cache-Control: only-if-cached
```

- 클라는 캐시 서버에 대해서 목적한 리소스가 로컬 캐시에 있는 경우만 리스폰스를 반환하도록 요구함
  - 캐시 서버에서 리스폰스의 리로드와 유효성을 재확인하지 않도록 요구함
- 캐시 서버가 로컬 캐시로부터 응답할 수 없는 경우에는 "504 Gateway Timeout" 상태를 반환함

_3)_ **must-revalidate 디렉티브**

```
Cache-Control: must-revalidate
```

- 리스폰스의 캐시가 현재도 유효한지 아닌지 여부를 오리진 서버에 조회를 요구함
- 프록시가 오리진 서버에 도달할 수 없고, 리소스를 다시 요구할 수 없는 경우에는 캐시가 클라에 504 Gateway Timeout를 반환함
- `must-revalidate` 디렉티브가 사용되는 경우, 리퀘스트에서 `max-stale` 디렉티브를 사용하고 있더라도 무시함

_4)_ **proxy-revalidate 디렉티브**

```
Cache-Control: proxy-revalidate
```

- 모든 캐시 서버에 대해 이후의 리퀘스트로 해당 리스폰스를 반환할 때는 반드시 유효성 재확인을 하도록 요구

_5)_ **no-transform 디렉티브**

```
Cache-Control: no-transform
```

- 리퀘스트와 리스폰스의 어느 쪽에 있어서도 캐시가 엔티티 바디의 미디어 타입을 변경하지 않도록 지정함
  - 이렇게 해서 캐시 서버 등에 의해 이미지가 압축되는 것을 방지함

**Cache-Control 확장**

_1)_ **cache-extension 토큰**

```
Cache-Control: private, community="UCI"
```

- Cache-Control 헤더 필드는 cache-extension 토큰을 사용하여 디렉티브를 확장할 수 있음
- 위 예와 같이 community라는 디렉티브는 Cache-Control 헤더 필드에는 없지만 extension tokens에 의해 추가할 수 있음
  - 만약 캐시 서버가 새로운 디렉티브 community를 이해하지 못할 경우 무시됨

## Connection

- Connection 헤더 필드는 다음 두 가지 역할을 함

_1._ **프록시에 더 이상 전송하지 않는 헤더 필드를 지정**

```
Connection: 더 이상 전송하지 않는 헤더 필드 명
```

- 클라의 리퀘스트 혹은 서버의 리스폰스에서 Connection 헤더 필드를 사용해 프록시 서버에 더 이상 전송하지 않는 헤더 필드(hop-by-hop 헤더)를 지정할 수 있음

_2._ **지속적 접속 관리**

```
Connection: Close
```

- HTTP/1.1에서는 지속적 접소이 디폴트로 되어 있음
  - 리퀘스트를 송신했던 클라는 접속이 계속 유지되면서 추가 리퀘스트를 송신하도록 함
- 서버 측에서 명시적으로 접속을 끊고 싶을 경우에는 Connection 헤더 필드에 Close라고 지정함

```
Connection: Keep-Alive
```

- HTTP/1.1 이전 버전의 HTTP에서는 지속적 접속이 디폴트가 아니었음
  - 그렇기 때문에 오래된 버전의 HTTP에서 지속적 접속을 하고 싶은 경우에는 Connection 헤더 필드에 `Keep-Alive`라고 지정해야 함

```
// 리퀘스트
GET / HTTP/1.1
Connection: Kepp-Alive

// 리스폰스
HTTP/1.1 200 OK
...
Keep-Alive: timeout=10, max=500
Connection: Keep-Alive
...
```

- 클라가 리퀘스트를 보낸 경우, 서버에서는 Keep-Alive 헤더 필드와 Connection 헤더 필드를 붙여서 리스폰스함

## Date

- Date 헤더 필드는 HTTP 메시지를 생성한 날짜를 나타냄
- HTTP/1.1에서는 RFC1123에 다음과 같이 날짜 포맷이 지정되어 있음

```
Date: <day-name>, <day> <month> <year> <hour>:<minute>:<second> GMT
Date: Tue, 03 Jul 12 04:40:59 GMT
```

- 오래된 버전의 HTTP에서는 RFC850에 정의된 다음과 같은 포맷을 사용함

```
Date: <day-name>, <day>-<month>-<year> <hour>:<minute>:<second> GMT
Date: Tue, 03-Jul-12 04:40:59 GMT
```

- 표준 C 라이브러리에 포함된 asctime() 함수의 출력 형식과 같음

```
Date: <day-name>, <month> <day> <hour>:<minute>:<second> <year> GMT
Date: Tue, Jul 03 04:40:59 2012
```

## Pragma

- HTTP/1.1보다 오래된 버전의 흔적으로 HTTP/1.0와의 후방 호환성만을 위해서 정의되어 있는 헤더 필드임
- 지정할 수 있는 형식은 다음과 같이 1개 뿐임

```
Pragma: no-cache
```

- 일반 헤더 필드이지만 클라의 리퀘스트에서만 사용됨
- 클라는 캐시된 리소스의 리스폰스를 원하지 않음을 모든 중간 서버에 알리기 위해 사용
- 모든 중간 서버가 HTTP/1.1을 기준으로 구성되어 있다면 `Cache-Control: no-cache`를 사용하는 것이 바람직하지만, 중간 서버의 HTTP 버전을 모두 파악한 후에 리퀘스트를 보내는 일은 현실적으로 없음
  - 그렇기 때문에 아래와 같이 양쪽을 보내는 경우도 있음

```
Cache-Control: no-cachePragma: no-cache
```

## Trailer

- 메시지 바디의 뒤에 기술되어 있는 헤더 필드를 미리 전달할 수 있음
- 이 헤더 필드는 HTTP/1.1에 구현되어 있는 청크 전송 인코딩을 사용하고 있는 경우에 사용 가능함

```
HTTP/1.1 200 OK
Date: Tue, 03, Jul 2012 04:40:56 GMT
Content-Type: text/html
...
Transfer-Encoding: chunked
Trailer: Expires
...(메시지 바디)...
0
Expires: Tue, 28 Sep 2004 23:59:59 GMT
```

- 이 예에서 Trailer 헤더 필드에 Expires를 지정하고 있고, 메시지 바디의 뒤(청크의 길이가 0의 뒤)에 Expires 헤더 필드가 나타나고 있음

## Transfer-Encoding

- 메시지 바디의 코딩 형식을 지정하는 경우에 사용됨
- HTTP/1.1에서 전송 코딩 형식으로 청크 전송만이 정의되어있음

```
HTTP/1.1 200 OK
Date: Tue, 03, Jul 2012 04:40:56 GMT
Cache-Control: public, max-age=604800
Content-Type: text/javascript; charset=utf-8
Expires: Tue, 10 Jul 2012 04:40:56 GMT
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block
Content-Encoding: gzip
Transfer-Encoding: chunked
Connection: keep-alive

Cf0 <- 16진수(10진수로 3312)
...3312bytes 정도의 chunk 데이터
392 <- 16진수(10진수로 914)
...914bytes 정도의 chunk 데이터
0
```

- 이 에의 경우, Transfer-Encoding 헤더 필드로 지정한 것처럼 청크 전송 코딩이 유효한 상태고, 3312 bytes와 912 bytes의 청크 데이터로 분할되어 있음

## Upgrade

- HTTP 및 다른 프로토콜의 새로운 버전이 통신에 이용되는 경우에 사용됨
- 지정하는 대상이 전혀 다른 통신 프로토콜이라고 하더라도 문제 없음

```
// 리퀘스트
GET /index.htm HTTP/1.1
Upgrade: TLS/1.0
Connection: Upgrade

// 리스폰스
HTTP/1.1 101 Switching Protocols
Upgrade: TLS/1.0, HTTP/1.1
Connection: Upgrade
```

- 이 예의 경우, Upgrade 헤더 필드에 TLS/1.0가 지정되어 있음
  - 양쪽 모두 Connection 필드가 지정되어 있는 것에 주목
- Upgrade 헤더 필드에 의해 업그레이드 되는 대상은 클라와 인접한 서버 사이 뿐이기 때문에 Upgrade 헤더 필드를 사용하는 경우는 `Connection: Upgrade`도 지정할 필요가 있음
- Upgrade 헤더 필드가 달린 리퀘스트에 대해서 서버는 상태 코드 101 Switching Protocols라는 리스폰스로 응답할 수 있음

## Via

- 클라와 서버 간 리퀘스트 혹은 리스폰스 메시지의 경로를 알기 위해 사용됨
- 프록시 혹은 게이트웨이는 자신의 서버 정보를 Via 헤더 필드에 추가한 뒤에 메시지를 전송함
  - 이것은 traceroute와 메일의 Received 헤더의 기능과 유사함
- 전송된 메시지의 추적과 리퀘스트 루프의 회피 등에 사용되기 때문에 프록시를 경유하는 경우에는 반드시 부가할 필요가 있음
- Via 헤더는 배송 경로를 알기 위해 TRACE 메소드와 연계해서 자주 사용됨

## Warning

- HTTP/1.0 리스폰스 헤더(Retry-After)가 HTTP/1.1에서 변경된 것으로, 리스폰스에 관한 추가 정보를 전달함
- 기본적으로 캐시에 관한 문제의 경고를 유저에 전달함

```
Warning: 113 gw.hackr.jp:8080 "Heuristic expiration"Tue, 03 Jul -> 2012 05:09:44 GMT
```

- Warning 헤더 형식은 다음과 같이 되어 있음
  - 마지막 날짜는 생략 가능

```
Warning: [경고 코드][경고한 호스트:포트 번호]"[경고문]" ([날짜])
```

- HTTP/1.1에는 7개의 경고 코드가 정의되어 있음
- 여기에 정의되어 있는 코드에 대한 경고문은 권장사항임
  - 경고 코드는 확장성을 가지고 있기 때문에 이후에 코드를 추가할 수 있음

HTTP/1.1 경고 코드

| 코드 | 경고문                           | 설명                                                         |
| ---- | -------------------------------- | ------------------------------------------------------------ |
| 110  | Response is Stale                | 프록시가 유효기한이 지난 리소스를 반환함                     |
| 111  | Revalidation Failed              | 프록시가 리소스의 유효성 재확인에 실패했음(서버에 도닥할 수 없는 등) |
| 112  | Disconnected Operation           | 프록시가 네트워크로부터 고의로 끊겨 있음                     |
| 113  | Heuristic Expiration             | 리스폰스가 24시간이상 경과하고 있는 경우(캐시의 유효기한을 24시간 이상으로 설정하고 있는 경우) |
| 199  | Miscellaneous Warning            | 임의의 경고문                                                |
| 214  | Transformation Applied           | 프록시가 인코딩과 미디어 타입 등에 대응해서 무언가의 처리를 한 경우 |
| 299  | Miscellaneous Persistent Warning | 임의의 경고문                                                |

# 6-4. 리퀘스트 헤더 필드

- 클라 측에서 서버 측으로 송신된 리퀘스트 메시지에 사용되는 헤더
- 리퀘스트의 부가 정보와 클라의 정보, 리스폰스의 콘텐츠에 관한 우선 순위 등을 추가함

## Accept

```
Accept: text/html, application/xhtml+xml, application/xml;q=0.9,*/*;q=0.8
```

- 유저 에이전트에 처리할 수 있는 미디어 타입과 미디어 타입의 상대적인 우선 순위를 전달하기 위해 사용
- 미디어 타입의 지정은 "타입/서브 타입"으로서 한 번에 여러 번 설정할 수도 있음

**미디어 타입은 다음과 같은 것들이 있음**

- **텍스트 파일**
  - text/html, text/plain, text/css ...
  - application/xhtml+xml, application/xml ...
- **이미지 파일**
  - image/jpeg, image/gif, image/png ...
- **동영상 파일**
  - video/mpeg, video/quicktime ...
- **애플리케이션용 바이너리 파일**
  - application/octet-stream, application/zip ...

- ex) 브라우저가 PNG 이미지를 표시하지 못하는 경우 Accept에 image/png를 지정하지 않고, 처리 가능한 image/gif와 image/jpeg 등을 지정하도록 함
- 표시하는 미디어 타입에 우선 순위를 붙이고 싶으면 ":" 으로  구분하고 "q="로 표시할 품질 지수를 더함
- 품질 계수는 0~1 범위의 소수점 3자리로, 1이 높은 쪽임
  - 품질 계수의 지정이 없는 경우에는 암묵적으로 "q=1.0"을 나타냄
- 서버가 복수의 콘텐츠를 반환할 수 있는 경우 가장 높은 품질 계수의 미디어 타입으로 반환할 필요가 있음

## Accept-Charset

```
Accept-Charset:iso-8859-5, unicode-1-1:q+0.8
```

- 유저 에이전트에서 처리할 수 있는 문자셋으로 문자셋의 상대적인 우선 순위를 전달하기 위해 사용됨
  - 문자셋은 한번에 여러 개를 지정할 수 있음
- Accept 헤더 필드와 마찬가지로 품질 지수에 의해 상대적 우선 순위를 표시함
- 이 헤더 필드는 서버 구동형 네고시에이션에 이용됨

## Accept-Encoding

```
Accept-Encoding: gzip, deflate
```

- 유저 에이전트가 처리할 수 있는 콘텐츠 코딩과 콘텐츠 코딩의 상대적인 우선 순위를 전달하기 위해 사용됨
  - 콘텐츠 코딩의 지정은 한번에 여러 개를 지정할 수 있음

**콘텐츠 코딩은 다음과 같은 것들이 있음**

- **gzip**
  - 파일 압축 프로그램 gzip(GNU zip)에서 생성된 인코딩 포맷(RFC1952)으로 Lempel-Ziv 부호(LZ77)와 32비트 CRC를 사용함
- **compress**
  - UNIX 파일 압축 프로그램 `compress` 에 의해 만들어진 인코딩 포맷으로 Lempel-Ziv-Welch 부호(LZW)를 사용함
- **deflate**
  - Zlib 포맷(RFC1950)과 deflate 압축 알고리즘(RFC1951)에 의해 만들어진 인코딩 포맷을 조합한 것
- **identify**
  - 압축과 변형을 하지 않는 디폴트 인코딩 포맷임
- Accept 헤더 필드와 같이 품질지수에 의해 상대적인 우선순위를 표시함
  - "*"(애스터리스크)를 지정하면 와일드 카드로서 모든 인코딩 포맷을 가리킴

## Accept-Language

```
Accept-Language: ko-kr. en-us;q=9.7,en:q=0.3
```

- 유저 에이전트가 처리할 수 있는 자연어의 세트(한국어와 영어)와 자연어 세트의 상대적인 우선 순위를 전달하기 위해 사용
  - 자연어 세트는 한번에 여러 개를 지정할 수 있음
- Accept 헤더 필드와 같이 품질 지수에 의해 상대적인 우선순위를 나타냄
- 위 예의 경우 한국어 리소스가 있는 경우에는 한국어로, 없으면 영어 리소스로 리스폰스를 받고 싶다는 것을 나타냄

## Authorization

```
Authorization: Basic ...
```

- 유저 에이전트의 인증 정보(크리덴셜 값)을 전달하기 위해 사용됨
- 통상, 서버에 인증을 받으려 하는 유저 에이전트는 상태 코드 401 리스폰스 뒤에 리퀘스트에 Authorization 헤더 필드를 포함함
- 공유 캐시가 Authorization 헤더 필드를 포함하는 리퀘스트를 받은 경우에는 조금 다르게 동작함

## Expect

```
Expect: 100-continue
```

- 클라가 서버에 특정 동작 요구를 전달
- 기대하고 있는 요구에 서버가 응답하지 못해 에러가 발생하는 경우 상태 코드 417 Expectation Failed를 반환함
- 클라는 이 헤더 필드에 원하는 확장을 딸려 보낼 수 있지만 HTTP/1.1의 사양에서는 100-continue(상태 코드 100 Continue의 의미)만 정의되어 있음
- 상태 코드 100 리스폰스를 가진 클라는 리퀘스트할 때 Expect:100-continue로 지정해야 함

## From

- 유저 에이전트를 사용하고 있는 유저의 메일 주소를 전달함
- 기본적으로 검색 엔진 등의 에이전트 책임자에게 연락처 메일 주소를 나타내는 목적으로 사용됨
- 에이전트를 사용하는 경우 되도록 From 헤더 필드를 포함해야함
  - 에이전트에 따라서는 User-Agent 헤더 필드에 메일 주소를 포함하고 있는 것도 있음

## Host

```
Host: www.hackr.ip
```

- 리퀘스트한 리소스의 인터넷 호스트와 포트 번호를 전달함
- Host 헤더 필드는 HTTP/1.1에서 유일한 필수 헤더 필드
- Host 헤더 필드가 존재하는 이유는 1대의 서버에서 복수의 도메인을 할당할 수 있는 가상 호스트의 구조와 매우 깊은 관련이 있음
- 리퀘스트가 서버에 오면 호스트 명을 IP 주소로 해결해 리퀘스트가 처리됨
- 이 때 같은 IP 주소로 복수의 도메인이 적용되어 있다고 한다면 어느 도메인에 대한 리퀘스트인지 알 수 없음
  - 그래서 Host 헤더 필드에 리퀘스트를 받을 호스트명을 명확하게 해둘 필요가 있음
- 서버에 호스트 명이 설정되어 있지 않는 경우에는 아래와 같이 값을 비워서 보냄

```
Host:
```

## If-Match

- "If-xxx" 서식의 리퀘스트 헤더 필드는 조건부 리퀘스트라고 부름
- 조건부 리퀘스트를 받은 서버는 지정된 조건에 맞는 경우에만 리퀘스트를 받음

```
If-Match: "123456"
```

- 조건부 리퀘스트의 하나로 서버 상의 리소스를 특정하기 위해 엔티티 태그(Etag) 값을 전달함
  - 이 때 서버는 약한 Etag 값을 사용할 수 없음
- 서버는 If-Match의 필드 값과 리소스의 ETag 값이 일치한 경우에만 리퀘스트를 받아들일 수 있음
- 일치하지 않으면 상태 코드 412 Precondition Failed 리스폰스를 반환
- If-Match 필드 값에 *를 지정할 수도 있음
  - 이 경우 ETag 값에 구애받지 않고 리소스가 존재하면 리퀘스트를 처리할 수 있음

## If-Modified-Since

```
If-Modified-Since: Thu, 15 Apr 2004 00:00:00 GMT
```

- 조건부 리퀘스트의 하나로 리스소가 갱신 날짜의 필드 값보다 새롭지 않다면 리퀘스트를 받아들이겠다는 뜻을 전달함
- 리소스가 갱신되어 있지 않은 경우 304 Not Modified 리스폰스를 반환함

## If-None-Match

- 조건부 리퀘스트의 하나로 If-Match와 반대로 동작
- 지정된 ETag 값이 지정된 리소스의 ETag 값과 일치하지 않으면 리퀘스트를 받아들이겠다는 뜻을 전달함
- GET과 HEAD 메소드에서 If-None-Match 헤더 필드를 사용함으로써 최신의 리소스를 요구하는 것이 되기 때문에 If-Modified-Since 헤더 필드를 사용하는 것과 비슷함

## If-Range

- 조건부 리퀘스트의 하나로 If-Range로 지정한 필드 값(ETag 값, 혹은 날짜를 지정)과 지정한 리소스의 ETag 값 혹은 날짜가 일치하면 Range 리퀘스트로서 처리하고 싶다는 것을 전달함
  - 일치하지 않으면 리소스 전체를 반환함
- If-Range 헤더 필드를 사용하지 않는 리퀘스트는 서버 측의 리소스가 갱신되어 있는 경우, 클라 측에서 가지고 있는 리소스의 일부분은 무효한 것이 되기 때문에 Range 리퀘스트는 당연히 무효함
  - 이 경우에 서버는 일단 상태 코드 412 Precondition Failed 리스폰스를 반환하고 클라에 다시 리퀘스트를 보내도록 재촉함
  - If-Range 헤더 필드를 사용하는 경우와 비교하면 2배의 수고가 필요함

## If-Unmodified-Since

```
If-Unmodified-Since: Thu, 03 Jul 2012 00:00:00 GMT
```

- If-Modified-Since와 반대로 동작함
- 지정된 리소스가 필드 값에 지정된 날짜 이후에 갱신되어 있지 않은 경우에만 리퀘스트를 받아들이도록 전달함
- 지정된 날짜 이후에 갱신된 경우에는 상태 코드 412 Precondition Failed 리스폰스를 반환함

## Max-Forwards

```
Max-Forwards: 10
```

- TRACE 혹은 OPTIONS 메소드에 의한 리퀘스트를 할 때에 전송해도 좋은 서버 수의 최대치를 10진수 정수로 지정함
- 서버는 다음 서버에 리퀘스트를 전송할 때는 Max-Forwards 값에서 1을 빼서 다시 세트함
- Max-Forwards 값이 0인 리퀘스트를 받은 경우에는 전송하지 않고 리스폰스를 반환할 필요가 있음
- HTTP를 사용한 통신에서는 리퀘스트가 프록시 서버 등 여러 대의 서버를 경유해 가는 경우가 있음
- 도중에 프록시 서버에서 무언가의 원인으로 리퀘스트 전송이 실패할 경우 클라에 리스폰스가 되돌아 오지 않기 때문에 알 수 없음
  - 이러한 문제 발생한 경우의 원인 조사에 Max-Forwards 헤더 필드는 활용됨
  - 필드 값이 0이 되었던 서버가 리스폰스를 하기 때문에 그 서버까지의 상황을 알 수 있음

## Proxy-Authorization

```
Proxy-Authorization: Basic ...
```

- 프록시 서버에서의 인증 요구를 받아들인 때에 인증에 필요한 클라의 정보를 전달함
- 클라와 서버의 HTTP 액세스 인증과 비슷한데 다른 점은 클라와 프록시 사이에 인증이 이루어진다는 것
- 클라와 서버의 경우, Authorization 헤더 필드와 같은 역할을 함

## Range

```
Range: bytes=5001-10000
```

- 리소스의 일부분만 취득하는 Range 리퀘스트를 할 때 지정 범위를 전달함
- Range 헤더 필드가 달린 리퀘스트를 받아들인 서버가 리퀘스트를 처리할 수 있는 경우 상태 코드 206 Partial Content 리스폰스를 반환함
- Range를 처리할 수 없는 경우에는 200 OK 리스폰스로 리소스 전체를 반환함

## Referer

- 리퀘스트가 발생한 본래 리소스의 URI를 전달함
- 기본적으로 Referer 헤더 필드는 보내져야 하지만, 브라우저의 주소창에 직접 URI를 입력한 경우와 보안상 바람직하지 않다고 판단된 경우에는 보내지 않아도 됨
- 본래 리소스의 URI의 쿼리에 ID 및 패스워드와 비밀 정보 등이 포함되어 있는 경우, Referer를 통해 그 정보가 다른 서버에 누설되어 버릴 가능성이있음
  - 또한 Referer 철자는 "Referrer"가 올바르지만, 잘못된 철차 그래도 사용되고 있음

## TE

```
TE: gzip, deflate;q=0.5
```

- 리스폰스로 받을 수 있는 전송 코딩의 형식과 우선 순위를 전달함
- Accept-Encoding 헤더 필드와 매우 비슷하지만 여기선 전송 코딩에 적용됨
- TE 헤더 필드는 전송 코딩 지정 이외에 Trailer를 동반하는 청크 전송 인코딩 형식을 지원하는 것도 가능
  - 이 경우, 필드 값에 "trailers"라고 기록함

```
TE: trailers
```

## User-Agent

```
User-Agent:Mozilla/5.0 ...
```

- 리퀘스트를 생성한 브라우저와 유저 에이전트의 이름 등을 전달하기 위한 필드
- 로봇 엔진의 리퀘스트의 경우 로봇 엔진의 책임자 메일 주소가 부가된 것도 있음
- 프록시 경유로 리퀘스트의 경우 프록시 서버의 이름 등이 부가된 것도 있음

# 6-5. 리스폰스 헤더 필드

- 서버 측으로부터 클라 측으로 송신되는 리스폰스 메시지에 적용된 헤더로 리스폰스의 부가 정보나 서버의 정보, 클라에 부가 정보 요구 등을 나타냄

## Accept-Ranges

```
Accept-Ranges: bytes
```

- 서버가 리소스의 일부분만 지정해서 취득할 수 있는 Range 리퀘스트를 접수할 수 있는지 여부를 전달함
- 지정 가능한 필드 값은 2개
  - 수신 가능한 경우 : `bytes`
  - 수신 불가능한 경우 : `none`

## Age

```
Age: 600(단위: 초)
```

- 얼마나 오래 전에 오리진 서버에서 리스폰스가 생성되었는지를 전달함
- 리스폰스한 서버가 캐시 서버라면, 캐시된 리스폰스가 다시 실증되었던 때부터 검증한 시간이 됨
- 프록시가 리스폰스를 생성했다면 Age 헤더 필드는 필수

## ETag

```
ETag: ...
```

- 엔티티 태그라고 불리며 일의적으로 리소스를 특정하기 위한 문자열을 전달함
- 서버는 리소스마다 ETag 값을 할당함
- 리소스가 갱신되면 ETag 값도 갱신할 필요가 있음
- ETag 값의 문자에는 특별히 룰이 정해져 있지 않고 서버에 따라 다양한 ETag 값을 할당함
- 리소스를 캐시할 때는 리소스를 일의적으로 정하고 싶은 상황이 있음
  - ex) 한국어 버전의 브라우저를 사용해서 액세스하면 한국어의 리소스가 반환되지만 영문판 브라우저를 사용해서 액세스하면 영어의 리소스를 반환함
  - 둘다 URI는 같지만 URI만으로는 캐시했었던 리소스를 특정하는 것은 어려움
- 도중에 다운로드가 끊겨서 다시 하는 경우에 ETag 값을 참조해서 리소스를 특정함

**강력한 ETag 값과 약한 ETag 값**

- ETag에는 강한(strong) ETag 값과 약한(weak) ETag 값으로 구별되어 있음

_1)_ **강한 ETag 값**

- 엔티티가 아주 조금 다르더라도 반드시 값은 변화함

```
ETag: "Usagi-1234"
```

_2)_ 약한 ETag 값

- 리소스가 같다는 것만을 나타냄
- 의미가 다른 리소스로 그 차이가 있는 경우에만 ETag 값이 변화함
- 값의 앞부분에 "W/"가 붙음

```
ETag: W/"usagi-1234"
```

## Location

```
Location: http://www....
```

- 리스폰스의 수신자에 대해서 Request-URI 이외의 리소스 액세스를 유도하는 경우에 사용
- 기본적으로 "3xx: Redirection"리스폰스에 대해서 리다이렉트 처의 URI를 기술함
- 대부분의 브라우저에서는 Location 헤더 필드를 포함한 리스폰스를 받으면 강제로 리다이렉트 하는 곳의 리소스에 액세스를 시도함

## Proxy-Authenticate

```
Proxy-Authenticate: Basic realm="Usagidesign Auth"
```

- 프록시 서버에서의 인증 요구를 클라에 전달함
- 클라와 서버와의 HTTP 액세스 인증과 비슷한데 다른점은 클라와 프록시 사이에서 인증이 이루어진다는 것
- 클라와 서버의 경우 WWW-Authorization 헤더 필드와 같은 역할을 함

## Retry-After

```
Retry-After: 120
```

- 클라가 일정 시간 후에 리퀘스틀르 다시 시행해야 하는지를 전달함
- 주로 상태 코드 503 Service Unavailable 리스폰스나 3xx Redirect 리스폰스와 함께 사용됨
- 값으로는 날짜(`<day-name>, <day> <month> <year> <hour>:<minute>:<second> GMT` 등의 형식)이라든가 리스폰스 이후의 몇 초를 지정할 수 있음

## Server

```
Server: Apache/2.2.17(Unix)
```

- 서버에 설치되어 있는 HTTP 서버의 소프트웨어를 전달함
- 서버의 소프트웨어 명칭만이 아닌 버전이나 옵션에 대해서도 기재하는 경우 있음

```
Server: Apache/2.2.6 (Unix) PHP/5.2.5
```

## Vary

```
Vary: Accept-Language
```

- 캐시를 컨트롤하기 위해서 사용
- 오리진 서버가 프록시 서버에 로컬 캐시를 사용한느 방법에 대해 지시를 전달함
- 오리진 서버로부터 Vary에 지정되었던 리스폰스를 받아들인 프록시 서버는 이후 캐시된 때의 리퀘스트와 같은 Vary에 지정되어 있는 헤더 필드를 가진 리퀘스트에 대해서만 캐시를 반환할 수 있음
- 같은 리소스에 대한 리퀘스라도 Vary에 지정되었던 헤더 필드가 다른 경우에는 오리진 서버로부터 리소스를 취득할 필요가 있음

## WWW-Authenticate

```
WWW-Authenticate: Basic realm="Usagidesign Auth"
```

- HTTP 액세스 인증에 사용되는데 Request-URI에 지정했던 리소스에 적용할 수 있는 인증 스키마("Basic"  or "Digest")와 파라미터를 나타내는 challenge를 전달함
- WWW-Authenticate 헤더 필드는 상태 코드 401 Unauthorized 리스폰스에 반드시 포함됨
- 이 예에서 "realm"는 Request-URI에 지정된 보호되었던 리소스를 식별하기 위한 문자열

# 6-6. 엔티티 헤더 필드

- 리퀘스트 메시지와 리스폰스 메시지에 포함된 엔티티에 사용되는 헤더로 콘텐츠의 갱신 시간 같은 엔티티에 관한 정보를 포함함

## Allow

```
Allow: GET, HEAD
```

- Request-URI에 지정된 리소스가 제공하는 메소드의 일람을 전달함
- 서버가 받을 수 없는 메소드를 수신한 경우에는 상태 코드 405 Method Not Allowed 리스폰스와 함께 수신 가능한 메소드의 일람을 기술한 Allow 헤더 필드를 반환함

## Content-Encoding

```
Content-Encoding: gzip
```

- 서버가 엔티티 바디에 대해서 실시한 콘텐츠 코딩 형식을 전달함
- 콘텐츠 코딩은 엔티니의 정보가 누락되지 않도록 압축할 것을 지시함

**4가지 콘텐츠 코딩 형식**

- Gzip
- Compress
- Deflate
- Identity

## Content-Language

```
Content-Language: en
```

- 엔티티 바디에 사용된 자연여(한국어, 영어 등)를 전달함

## Content-Length

```
Content-Length: 15000
```

- 엔티티 바디의 크기(단위: bytes)를 전달함
- 엔티티 바디에 전송 코딩이 실시된 경우에는 Content-Length 헤더 필드를 사용해서는 안됨

## Content-Location

```
Content-Location: http://www....
```

- 메시지 바디에 대응하는 URI를 전달함
- Location 헤더 필드와 달리 Content-Location은 메시지 바디로 반환된 리소스의 URI를 나타냄

## Content-MD5

```
Content-MD5: ...
```

- 메시지 바디가 변경되지 않고 도착했는지 확인하기 위해 MD5 알고리즘에 의해서 생성된 값을 전달함
- 메시지 바디에 MD5 알고리즘을 적용해서 얻은 128비트의 바이너리 값에 Base64 인코딩을 한 결과를 필드 값에 기록함
  - HTTP 헤더에는 바이너리 값을 기록하는 것이 불가능해서 Base64로 인코딩함
- 유효성 확인을 위해 수신한 클라 측에서 메시지 바디에 같은 MD5 알고리즘 실행함
  - 이렇게 해서 도출한 값과 필드 값을 비교하여 메시지 바디가 올바른지 여부를 알 수 있음
- 이 방식에는 우발적으로콘텐츠가 변경되어 버린 사실을 알 수 있지만 악의를 가진 변조는 검출할 수 없음
  - 그 이유는 콘텐츠를 변조하면 Content-MD5도 재계산해서 변조하는 것이 가능함
- 클라가 수신한 단계에서는 메시지 바디도 Content-MD5 헤더 필드도 변조되어 있기 때문에 발견할 방법이 없음]

## Content-Range

```
Content-Range: bytes 5001-10000/10000
```

- 범위를 지정해서 일부부만을 리퀘스트하는 Range 리퀘스트에 대해서 리스폰스를 할 때에 사용됨
- 리스폰스로 보낸 엔티티가 어느 부분에 해당하는가를 전달함
- 필드 값에는 현재 보내고 있는 곳을 바이트로 지정한 범위와 전체 사이즈를 기록함

## Content-Type

```
Content-Type: text/html; charset=UTF-8
```

- 엔티티 바디에 포함되는 오브젝트의 미디어 타입을 전달함
- Accept 헤더 필드와 같이, 필드 값은 "타입/서브 타입"으로 기록함
- Charset 파라미터는 "iso-8859-1"과 "euc-kr" 등의 문자셋을 지정함

## Expires

````
Expires: Web, 04 Jul 2012 08:26:05 GMT
````

- 리소스의 유효 기한 날짜를 전달함
- 캐시 서버가 Expires 헤더 필드를 포함한 리소스를 수신한 경우 필드 값으로 지정된 날짜까지 리스폰스의 복사본을 유지하고 리퀘스트에는 캐시로 응답함
- 지정 날짜가 지난 경우에는 리퀘스트가 온 단계에서 오리진 서버에 리소스를 얻으러 감
- 오리진 서버가 캐시 서버에 캐시되는 것을 원하지 않을 경우에는 Date 헤더 필드의 필드 값과 같은 날짜로 해두는 것이 바람직함
  - 다만 Cache-Control 헤더 필드에 max-age 디렉티브가 지정되어 있는 경우에는 Expires 헤더 필드보다 max-age 디렉티비의 지정이 우선이됨

## Last-Modified

```
Last-Modified: Web, 23 May 2012 09:59:55 GMT
```

- 리소스가 마지막으로 갱신되었던 날짜 정보를 전달함
- 기본적으로 Request-URI가 지정된 리소스가 갱신되었던 날짜가 되지만 CGI 등의 스크립트로 동적인 데이터를 다룰 경우에는 그 데이터의 최종 갱신 날짜가 되는 경우도 있음

# 6-7. 쿠키를 위한 헤더 필드

- 서버와 클라이언트 간의 상태를 관리하는 쿠키는 HTTP/1.1의 사양인 RFC2616에 포함된 것은 아니지만 웹 사이트에서 널리 사용되고 있음
- 쿠키는 유저 식별과 상태 관리에 사용되고 있는 기능임
- 웹 사이트가 유저의 상태를 관리하기 위해서 웹 브라우저 경유로 유저의 컴퓨터 상에 일시적으로 데이터를 기록해 두고, 다음에 그 유저가 웹 사이트에 액세스 해 왔을 때 지난번에 발행된 쿠키를 송신받을 수 있음
- 쿠키가 호출되었을 때는 쿠기의 유효 기한과 송신지의 도메인, 경로, 프로토콜 등을 체크하는 것이 가능
  - 적절하게 발행된 쿠키는 다른 웹 사이트와 공격자의 공격에 의해 데이터가 도난당하는 일은 없음

## Set-Cookie

```
Set-Cookie: status-enable; expires=Tue, 05 Jul 2011 07:26:31 GMT; =>path=/;domain=.hack.jp;
```

- 서버가 클라에 대해서 상태 관리를 시작할 때 다양한 정보를 전달함

*Set-Cookie 필드 속성*

| 속성             | 설명                                                         |
| ---------------- | ------------------------------------------------------------ |
| NAME=VALUE       | 쿠키에 부여된 이름과 값(필수)                                |
| Expires=DATE     | 쿠기 유효 기한<br>(지정되지 않은 경우는 브라우저를 닫을 때까지) |
| Path=PATH        | 쿠키 적용 대상이 되는 서버 상의 디렉토리<br>(지정하지 않은 경우는 도큐먼트와 같은 디렉토리) |
| Domain=도메인 명 | 쿠키 적용 대상이 되는 도메인 명<br>(지정하지 않은 경우는 쿠키를 생성한 서버의 도메인) |
| Secure           | HTTPS로 통신하고 있는 경우에만 쿠키를 송신                   |
| HttpOnly         | 쿠키를 JavaScript(자바스크립트)에서 액세스하지 못하도록 제한 |

_1)_ **Expires 속성**

- 쿠키의 Expires 속성은 브라우저가 쿠키를 송출할 수 있는 유효 기한을 저정할 수 있음
- Expires 속성을 생략한 경우에는 브라우저 세션이 유지되고 있는 동안만 유효하게 됨
  - 이것은 통상은 브라우저 애플리케이션을 닫을 때까지
- 한번 서버에 송출한 클라의 쿠키는 서버에서 명시적으로 삭제하는 방법은 없음
- 유효 기한이 지났다면 쿠키를 덮어 쓰는 것으로 실질적으로 클라 측의 쿠키를 삭제하는 것이 가능

_2)_ **Path 속성**

- 쿠키의 path 속성은 쿠키를 송출하는 범위를 특정 디렉토리에 한정할 수 있음
- 이 지정을 피하는 방법이 있어서 보안 효과는 기대할 수 없음

_3)_ **Domain 속성**

- 쿠키의 domain 속성에 의해서 지정된 도메인 명은 후방 일치가 됨
  - ex) "example.com"로 지정했을 때 "example.com" 이외에 "www.example.com"과 "www2.example.com" 등에서도 쿠키가 송출됨
- 명시적으로 여러 도메인에 대해서 쿠키를 송출하는 경우를 제외하고 domain 속성은 지정하지 않는 쪽이 안전함

_4)_ **Secure 속성**

- 웹 페이지가 HTTPS에서 열렸을 때에만 쿠키 송출을 제한히기 위해서 지정함

```
Set-Cookie: name=value; secure
```

- 위의 경우 "https://www.example.com/(HTTPS)"일 때만 쿠키 반속을 함
  - 도메인이 같더라도 "http://www.example.com/(HTTP)"에는 쿠키 반송을 하지 않음
- secure 속성을 생략하는 경우에는 HTTP와 HTTPS에서도 쿠키를 반송함

_5)_ **HttpOnly 속성**

- 자바스크립트를 경유해서 쿠키를 취득하지 못하도록 하는 쿠키의 확장 기능임
- 크로스 사이트 스크립팅(XSS)으로부터 쿠키의 도청을 막는 것을 목적으로 함

```
Set-Cookie: name=value; HttpOnly
```

- 위의 경우, 통상 웹 페이지 내에서는 쿠키를 읽어 들이는 것은 가능하지만 HttpOnly 속성이 부여된 쿠키는 Javascript의 [document.cookie]에서는 읽어들일 수 없게됨
  - 그렇기 때문에 XSS에서 Javascript를 이용해 쿠키를 훔칠 수 없음
- 독자적으로 확장한 기능이지만 인터넷 익스플로러 6 SP1 이상의 브라우저를 비롯한 현재 주요한 브라우저에서는 거의 모두 대응하고 있음
- XSS 자체를 막는 것은 아님

## Cookie

```
Cookie: status=enable
```

- 클라가 HTTP의 상태 관리 지원을 원할 때 서버로부터 수신한 쿠키를 이후의 리퀘스트에 포함해서 전달함
- 쿠키를 여러 개 수신하고 있을 때에는 쿠키를 여러 개 보내는 것도 가능

# 6-8. 그 이외의 헤더 필드

- HTTP 헤더 필드는 독자적으로 확장할 수 있음
  - 그렇기 때문에 웹 서버와 브라우저의 기능에 다양한 독자적인 헤더 필드가 존재함

**자주 사용되는 헤더 필드**

- **X-Frame-Option**
- **X-XSS-Protection**
- **DNT**
- **P3P**

_1)_ **X-Frame-Option**

```
X-Frame-Option: DENY
```

- 다른 웹 사이트의 프레임에서 표시를 제어하는 HTTP 리스폰스 헤더로, 클릭 재킹(click jacking)이라는 공격을 막는 것을목적으로 함

**X-Frame-Option 헤더 필드에 지정할 수 있는 값**

- **DENY** : 거부
- **SAMEORIGIN** : Top-level-browsing-context가 일치한 경우에만 허가

- X-Frame-Option는 모든 웹 서버에서 설정해두는 것이 바람직함

```
<IfModule mod_headers.c>
	Header append X-FRAME-OPTIONS"SAMEORIGIN"
<IfModule>
```

## X-XSS-Protection

```
X-XSS-Protection: 1
```

- 크로스 사이트 스크립팅(XSS) 대책으로서 브라우저의 XSS 보호 기능을 제어하는 HTTP 리스폰스 헤더 임

**X-XSS-Protection 헤더 필드에 지정할 수 있는 값**

- **0** : XSS 필터를 무효로 함
- **1** : XSS 필터를 유효로 함

## DNT

```
DNT: 1
```

- Do No Track(DNT)라는 뜻이며 개인 정보 수집을 거부하는 의사를 나타내는 HTTP 리퀘스트 헤더임
- 타깃 광고 등에 이용되는 트래킹의 거부 의사를 나타내기 위한 방법 중 하나

**DNT 헤더 필드는에 지정할 수 있는 값**

- **0** : 트래킹 동의
- **1** : 트래킹 거부

- DNT 헤더 필드의 기능이 유효성을 유지하기 위해서는 웹 서버에서 DNT를 지원해야 할 필요가 있음

## P3P

```
P3P: CP="CAO DSP LAW CURa ADMa DEVa TAIa PSAa PSDa IVAa IVDa OUR BUS IND UNI COM NAV INT"
```

- 웹 사이트 상의 프라버시 정책에 P3P(The Platform for Privacy Preferences)를 사용하는 것으로, 프로그램이 읽을 수 있는 형태로 나타내기 위한 HTTP 리스폰스 헤더임

**P3P 설정 순서**

- **수순-1** : P3P 정책 작성
- **수순-2** : P3P 정책 참조 파일을 작성해서 "/w3c/p3p.xml"에 배치
- **수순-3** : P3P 정책으로부터 콤팩트 정책을 작성하고 HTTP 리스폰스 헤더에 출력

# reference

> [그림으로 배우는 HTTP & Network Basic](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=51908132)<br>
> [MDN Web Docs-HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP)
