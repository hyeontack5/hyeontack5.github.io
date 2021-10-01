---
title: "[Network] 결과를 전달하는 HTTP 상태 코드"
excerpt: "<!--more-->"
categories:
  - Network
tags:
  - Network
  - 그림으로 배우는 HTTP & Network Basic
toc: true
toc_sticky: true
toc_label: "[Network] 결과를 전달하는 HTTP 상태 코드"
toc_icon: "bookmark"
---

# 4-1. 상태 코드는 서버로부터 리퀘스트 결과를 전달
- **상태 코드**
  - 클라이언트가 서버로 리퀘스트 보낸 결과 서버에서 그 결과를 리스폰스로 알려주는 것

- 상태 코드 클래스

||클래스|설명|
|---|---|---|
|1xx|Informational|리퀘스트를 받아들여 처리중|
|2xx|Success|리퀘스트를 정상적으로 처리했음|
|3xx|Redirection|리퀘스트를 완료하기 위해서 추가 동작이 필요|
|4xx|Client error|서버는 리퀘스트 이해 불가능|
|5xx|Server Error|서버는 리퀘스트 처리 실패|

# 4-2. 2xx 성공(Success)

**4.2.1 200 OK**
- 클라이언트가 보낸 리퀘스트를 서버가 정상 처리되었음
- 리스폰스에 상태 코드와 되돌아 오는 정보는 **메소드**에 따라 다름
  - GET 메소드 : 리퀘스트된 리소스에 대응하는 엔티티가 리스폰스로 보내짐
  - HEAD 메소드 : 리퀘스트된 리소스에 대응하는 엔티티 헤더 필드가 메시지 바디를 동반하지 않고 리스폰스로 되돌아감

**4.2.2 204 No Content**
- 서버가 리퀘스트를 받아서 처리하는데 성공했지만 리스폰스에 엔티티 바디를 포함하지 않음
  - 클라이언트에서 서버에 정보를 보내는 것으로 족하고, 클라이언트에 새로운 정보를 보낼 필요 없는 경우에 사용

**4.2.3 206 Partial Content**
- Range로 범위가 지정된 리퀘스트에 의해 서버가 부분적 GET 리퀘스트를 받았음을 나타냄
- 리스폰스에는 Content-Range로 지정된 범위의 엔티티가 포함됨

# 4-3. 3xx 리다이렉트(Redirection)

**4.3.1 301 Moved Permanently**

**4.3.2 302 Found**
- 리퀘스트된 리소스에는 새로운 URI가 할당되어 있어 그 URI를 참조하라는 의미
  - 영구적인 이동이 아닌 일시적인 것

**4.3.3 303 See Other**
- 리퀘스트 대한 리소스는 다른 URI에 있기 때문에 GET 메소드를 사용해서 얻어야 함

# 4-4. 4xx 클라이언트 에러(Client Error)

**4.4.1 400 Bad Request**
- 리퀘스트 구문이 잘못되었음을 나타냄
  - 리퀘스트 내용을 재검토하고 나서 재송신할 필요가 있음
- 브라우저는 이것을 200 OK로 취급함

**4.4.2 401 Unauthorized**

**4.4.3 403 Forbidden**
- 리퀘스트된 리소스의 액세스가 거부되었음을 나타냄
  - 서버 측의 거부 이유를 명확하게 할 경우 엔티티 바디에 넣어 유저 측에 표시함

# reference

> [그림으로 배우는 HTTP & Network Basic](https://www.aladin.co.kr/shop/wproduct.aspx?ItemId=51908132)
[HTTP 상태코드](https://velog.io/@dnstlr2933/HTTP-%EC%83%81%ED%83%9C%EC%BD%94%EB%93%9C)
[REST API 관점에서 바라보는 HTTP 상태 코드](https://sanghaklee.tistory.com/61)