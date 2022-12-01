---
layout: default
title: CORS(교차 출처 리소스 공유)
parent: 튜토리얼
nav_order: 3
---

날짜 : 2022. 11. 29 (화)  
시간 : 오후 7시 ~ 오후 10시 (3시간)  
작성자 : 박경서

미팅을 진행할 때 서버측에서 CORS를 허용하지 않아, 개발에 문제가 발생하였다고 한다.

CORS 에 대한 자세한 설명은 인터넷에 많이 나와있다.

설명은 잘 나와 있지만, 해결 방법에 대해서는 자세히 나와있지가 않다.

그래서 작성하게 되었다.

# CORS 란 무엇인가

클라이언트가 서버에 API 를 요청했을 때 도메인이 다른 경우 **브라우저에서 차단하는 보안**이다.

- 서버에서 서버로 요청할 경우 CORS 는 발생하지 않는다.
- 포스트맨에서 요청할 경우 CORS 는 발생하지 않는다. (포스트맨은 브라우저가 아니니까)

도메인이 다른 경우의 예시

```json
# 도메인이 다르다.
"https://kspark.link": "https://kkyungvelyy.com"

# 서브 도메인이 다르다.
"https://front.kspark.link": "https://api.kspark.link"
```

---

## CORS 해결 방법

CORS 를 해결하는 방법은 3가지가 있다. (내가 알고있는 방법)

- Proxy 를 통해 클라이언트와 서버의 도메인을 동일하게 만든다.
- Nginx, Apache 등 웹 엔진에서 클라이언트의 도메인을 허용한다. (Response Header 에 추가)
- 서버에서 클라이언트의 도메인을 허용한다. (Response Header 에 추가)

---

## 개발할 때 CORS 임시 허용하기

크롬을 사용한다면, 크롬 확장도구를 사용한다.

- 크롬을 사용한다면, 크롬 확장도구 [Allow CORS: Access-Control-Allow-Origin](https://chrome.google.com/webstore/detail/allow-cors-access-control/lhobafahddgcelffkeicbaginigeejlf?hl=en)를 사용한다.

- proxy 를 통해 API Endpoint 주소 바꾸기

```javascript
// http-proxy-middleware
const { createProxyMiddleware } = require("http-proxy-middleware");

module.exports = function (app) {
  // 'http://localhost/api' 로 요청하면 'http://apiserver:5000/api' 에 도착하게 된다.
  app.use(
    "/api",
    createProxyMiddleware({
      target: "http://apiserver:5000",
      changeOrigin: true,
      ws: true,
    })
  );
  // 웹소켓은 약간 다르다.
  app.use(
    createProxyMiddleware(["/socket.io"], {
      target: "http://apiserver:5000",
      changeOrigin: true,
      ws: true,
      router: {
        "/socket.io": "ws://apiserver:5000",
      },
    })
  );
};
```

- package.json 에 프록시 추가하기

```json
  // package.json
  {
  ...,
  "proxy": "http://apiserver.com:5000",
  ...,
  }

```
