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
// 리퀘스트GET / HTTP/1.1Connection: Kepp-Alive// 리스폰스HTTP/1.1 200 OK...Keep-Alive: timeout=10, max=500Connection: Keep-Alive...
```

- 클라가 리퀘스트를 보낸 경우, 서버에서는 Keep-Alive 헤더 필드와 Connection 헤더 필드를 붙여서 리스폰스함

## Date

- Date 헤더 필드는 HTTP 메시지를 생성한 날짜를 나타냄
- HTTP/1.1에서는 RFC1123에 다음과 같이 날짜 포맷이 지정되어 있음

```
Date: <day-name>, <day> <month> <year> <hour>:<minute>:<second> GMTDate: Tue, 03 Jul 12 04:40:59 GMT
```

- 오래된 버전의 HTTP에서는 RFC850에 정의된 다음과 같은 포맷을 사용함

```
Date: <day-name>, <day>-<month>-<year> <hour>:<minute>:<second> GMTDate: Tue, 03-Jul-12 04:40:59 GMT
```

- 표준 C 라이브러리에 포함된 asctime() 함수의 출력 형식과 같음

```
Date: <day-name>, <month> <day> <hour>:<minute>:<second> <year> GMTDate: Tue, Jul 03 04:40:59 2012
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
HTTP/1.1 200 OKDate: Tue, 03, Jul 2012 04:40:56 GMTContent-Type: text/html...Transfer-Encoding: chunkedTrailer: Expires...(메시지 바디)...0Expires: Tue, 28 Sep 2004 23:59:59 GMT
```

- 이 예에서 Trailer 헤더 필드에 Expires를 지정하고 있고, 메시지 바디의 뒤(청크의 길이가 0의 뒤)에 Expires 헤더 필드가 나타나고 있음

## Transfer-Encoding

- 메시지 바디의 코딩 형식을 지정하는 경우에 사용됨
- HTTP/1.1에서 전송 코딩 형식으로 청크 전송만이 정의되어있음

```
HTTP/1.1 200 OKDate: Tue, 03, Jul 2012 04:40:56 GMTCache-Control: public, max-age=604800Content-Type: text/javascript; charset=utf-8Expires: Tue, 10 Jul 2012 04:40:56 GMTX-Frame-Options: DENYX-XSS-Protection: 1; mode=blockContent-Encoding: gzipTransfer-Encoding: chunkedConnection: keep-aliveCf0 <- 16진수(10진수로 3312)...3312bytes 정도의 chunk 데이터392 <- 16진수(10진수로 914)...914bytes 정도의 chunk 데이터0
```

- 이 에의 경우, Transfer-Encoding 헤더 필드로 지정한 것처럼 청크 전송 코딩이 유효한 상태고, 3312 bytes와 912 bytes의 청크 데이터로 분할되어 있음

## Upgrade

- HTTP 및 다른 프로토콜의 새로운 버전이 통신에 이용되는 경우에 사용됨
- 지정하는 대상이 전혀 다른 통신 프로토콜이라고 하더라도 문제 없음

```
// 리퀘스트GET /index.htm HTTP/1.1Upgrade: TLS/1.0Connection: Upgrade// 리스폰스HTTP/1.1 101 Switching ProtocolsUpgrade: TLS/1.0, HTTP/1.1Connection: Upgrade
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

# reference

> [그림으로 배우는 HTTP & Network Basic](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=51908132)
> [MDN Web Docs-HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP)
