---
layout: default
title: CSR과 SSR
parent: 튜토리얼
nav_order: 7
---

CSR과 SSR

## 초창기 웹 렌더링
- 모든 웹페이지가 정적인 페이지
- 화면을 전환하면, 그 때마다 서버로부터 새로운 HTML을 전송 받아서 다시 렌더링 
→ 사용자 경험 측면에서 좋지 않음
<br>

&nbsp;&nbsp;&nbsp;&nbsp; **Ajax(Asynchronous JavaScript and XML) 등장**
* Javascript를 통해서 서버와 클라이언트가 비동기로 데이터 전달 가능
- 매번 전체 페이지에 대한 데이터를 가져올 필요없이 필요한 부분의 데이터만 불러와서 동적으로 웹 페이지 화면 변경
→ 서버에서만 이루어지던 다양한 로직 처리나 HTML 생성을 클라이언트에서도 처리 할 수 있게 되었음
- 복잡하고 거대해진 웹 어플리케이션을 보다 쉽게 구축할 수 있도록 도와주는 React, Vue, Angular 등의 프레임워크가 활발하게 사용

<br>
<br>

## CSR(Client Side Rendering)
![](https://velog.velcdn.com/images/kimjihong9/post/a4ebc5ca-4fa5-4afa-9180-5b6db5fadafc/image.png)

- 클라이언트가 서버에게 HTML과 JS파일을 요청한 후 로드되면 사용자의 상호작용에 따라 JS를 이용해서 동적으로 렌더링
- 클라이언트는 최초에 HTML을 받는 것 외에 페이지 렌더링을 위해 별도의 HTTP 통신을 할 필요 없음 

**👍 장점** <br>
→ 초기 로딩 이후 구동 속도가 빠르게 렌더링 되기 때문에 UX(사용자 경험) 향상 <br>
→ 서버에 요청하는 횟수가 훨씬 적어지기 때문에 서버의 부담이 덜함 <br>
→ TTV 와 TTI 사이 간극 없음


> ❓ 
TTV(Time To View): 사용자가 웹 브라우저에서 내용을 볼 수 있는 시점
TTI(Time To Interact): 사용자가 웹 브라우저에서 인터랙션 할 수 있는 시점

**👎 단점** <br>
→ 검색 엔진의 검색 봇이 크롤링하는데 어려움을 겪기 때문에 검색엔진 최적화(Search Engine Optimization) 에 불리 <br>
 &nbsp; 구글 봇의 경우 JS를 지원하지만, 다른 검색 엔진의 경우 그렇지 않기 때문에 문제 발생 <br>
→ 모든 스크립트 파일이 로드될 때까지 기다려야 하기 때문에 초기 로딩 속도 느림 <br>
 &nbsp; 리소스를 chunk 단위로 묶어서 요청할 때만 다운 받게 하는 방식으로 완화할 수 있지만 완벽하게 해결 불가능 <br>
>❓ SEO (Search Engine Optimization): 
웹사이트가 유기적인 검색 방식을 통해 검색 엔진에서 상위에 노출될 수 있도록 최적화하는 과정. 비즈니스 유형이 어떤 것이든 가장 중요한 마케팅 유형 중 하나

> ❓ chunk:
모든 코드를 하나의 거대한 파일(Bundle)로 만들지 않기 위해 여러 개의 chunk 라는 단위로 나눔. 코드가 나뉘는 방법에 대해 임의로 구성 가능


<br>

### SPA(Single Page Application) 
- CSR 렌더링 방식. 하나의 HTML 파일을 기반으로 JavaScript를 이용해 화면 컨텐츠를 동적으로 바꾸는 방식의 웹 어플리케이션
- 매번 서버에 접속할 필요없음
- 새로고침 되는 것이 아니라 router를 사용하여 페이지 이동
- 웹앱처럼 보여지며 페이지 이동, 페이지 전환이 빠름

<br>
<br>

## SSR(Server Side Rendering)
![](https://velog.velcdn.com/images/kimjihong9/post/d7bea97c-7154-4a61-bf05-98f8eec647b0/image.png)

- 클라이언트가 서버에게 페이지를 요청할 때마다 해당 페이지에 관련된 HTML, CSS, JS 파일 및 데이터를 받아와서 렌더링
- 이미 페이지 로드에 필요한 데이터를 서버에서 불러왔기 때문에 클라이언트 사이드에서 별도의 JavaScript 코드를 불러올 필요없음 → 첫 페이지 로딩 빠름

**👍 장점** <br>
→ 초기 로딩 속도가 빠름. 사용자가 컨텐츠를 빨리 볼 수 있음 <br>
→ 검색엔진 최적화(SEO)에 유리 <br>

**👎 단점** <br>
→ SPA에 비해 UX 저하 <br>
→ 매번 서버로부터 페이지를 전달받기 때문에 페이지를 생성하는 시간 소요됨 <br>
→ 매번 서버에게 요청하기 때문에 서버의 부하가 커질 수 있으며, 서버 비용이 많이 듬 <br>
→ TTV와 TTI 사이 간극 발생 <br>

<br>

### MPA(Multiple Page Application) 
- SSR 방식. 사용자가 페이지를 요청할 때마다 서버로부터 완전하게 만들어진 HTML파일을 받아와 전체를 바꾸는 방식의 웹 어플리케이션
<br>
<br>



*References:*
https://github.com/baeharam/Must-Know-About-Frontend/blob/main/Notes/frontend/csr-ssr.md
https://velog.io/@eeeve/%EC%9B%B9-%EB%A0%8C%EB%8D%94%EB%A7%81-%EB%B0%A9%EC%8B%9D-CSR-SSR-SSG
https://medium.com/walmartglobaltech/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8
