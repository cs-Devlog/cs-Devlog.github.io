---
title: HTTP와 REST API, Cookie, Session
date: 2019-05-21- 17:00:00
description: HTTP 프로토콜과 REST API, Cookie, Session에 대해 알아보자.
categories:
- Network
tags: 
- Network
- HTTP
- REST
- Cookie
- Session
---
# HTTP(HyperText Transfer Protocol)이란?
- 인터넷에서 데이터를 주고받을 수 있는 프로토콜로 웹 서버와 클라이언트간 통신하기 위한 규약
- 어느 종류의 데이터든지 전송할 수 있도록 설계되어있다. HTML 뿐만아니라 이미지, 동영상, 오디오, 텍스트 문서 등 종류를 가리지 않는다. 
- 이름 그대로 하이퍼텍스트를 기반으로 데이터를 전송하겠다는 말이다. 간단히 말하면 링크기반으로 데이터에 접속하겠다는 의미이다.

***

# HTTP 작동 방식
- TCP/IP를 사용하는 응용 프로토콜이며 HTTP 메세지는 HTTP 서버와 HTTP 클라이언트가 해석한다.
- HTTP는 연결 상태를 유지하지 않는 프로토콜이기 때문에 서버에 연결하고 Request에서 Response를 받으면 연결을 끊어버린다.

- **장점** : 수십만명이 웹 서비스를 사용하더라도 접속유지는 최소한으로 할 수 있기 때문에, 더 많은 유저의 요청을 처리 할 수 있다.
- **단점** : 연결을 끊어버리기 때문에 클라이언트의 이전 상태를 알 수 없다. 이를 위해 Cookie를 사용한다.

![web_process](/assets/images/network_http.png){: width="500"}

- 크롬 개발자도구의 네트워크 탭의 정보를 해석해보자.
- 요청한 URL은 <http://sophia2730.tistory.com> 이며 200 코드로 성공적인 요청이였다는 결과를 받았다.
- 여기서 작동한 Method는 GET이며 POST, PUT(수정) 등의 메소드를 사용하여 클라이언트와 서버가 데이터를 주고받는다.
- 여기서 URI를 자원으로 보고 Method를 동사로 보는 개발 방식이 REST 방식이다.

***

# REST API란?
- 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일로, 자원을 표현으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미한다.
- 즉, URI를 통해 자원(Resource)을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미한다.

- REST API는 두 가지 특징을 가진다.
1. URI는 정보의 자원을 표현해야 한다.  ex) GET /members/delete/1 (X),  DELETE /members/1 (O)
2. 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE)로 표현한다.

이러한 방식으로 확장성과 재사용성을 높여 유지보수 및 운용을 편리하게 할 수 있다.

***

# Cookie와 Session
## Cookie
- 모든 내용이 클라이언트측에서 저장되며 서버에 요청할 때 마다 HTTP 헤더에 쿠키 내용(**KEY=VALUE**)을 전달합니다.

![web_process](/assets/images/web_cookie.png){: width="500"}

1. 최초 접속일 경우 사용자ID, 로그인시간, IP등을 암호화한 구문을 클라이언트의 쿠키에 **KEY=VALUE** 된 구문으로 생성해 클라이언트에게 쿠키에 저장하라고 응답합니다. (예 : state=ASKHDNxxu7432keedsa7jhklsadasdmslk )
2. 클라이언트는 매번 서버에 요청할 때 위 쿠키를 전달합니다.
3. 서버는 로그인상황을 검사하기 위해서 매번 쿠키를 읽습니다. 그리고 위의 키를 찾아 정보를 해독하고, 서버에 있는 사용자 정보와 비교해 일치하면 로그인된 것으로 보고, 일치하지 않으면 불량요청 혹은 로그인하지 않은 사용자로 판별합니다.

## Session
- Session은 서버쪽에 저장되는 쿠키이며 클라이언트가 서버에 Request를 보내면 서버는 클라이언트한테 세션 ID를 제공한다.

![web_process](/assets/images/web_session.png){: width="500"}

1. 로그인 요청이 들어왔을 때 정보가 일치하면 서버는 사용자ID, 로그인시간, IP 등을 저장하는 Session을 생성합니다.
2. 클라이언트에 응답할 때 세션을 찾을 수 있는 Session ID를 클라이언트에 전달합니다.(보통 쿠키로 전달)
3. 클라이언트는 다음 요청시, Session ID를 함께 요청(쿠키를 사용하든 다른 방법을 사용하든)합니다.
4. 서버가 요청을 받은 경우 Session ID를 이용해서 서버에 저장된 세션을 찾아와 로그인을 확인할 수 있습니다.

## Cookie와 Session의 저장 정보와 위치

![web_process](/assets/images/cookie-session.png){: width="500"}

***

# 참고 
- <https://message0412.tistory.com/entry/HTTP-프로토콜-알아보기1>
- <https://hashcode.co.kr/questions/3243>
