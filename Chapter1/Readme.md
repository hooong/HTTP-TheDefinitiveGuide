# 1장 HTTP 개관

> 이번 장에서는 HTTP에 대하여 간결하게 설명한다. 가령 얼마나 많은 클라이언트와 서버가 통신하는지, 리소스가 어디서 오는지, 웹 트랜잭션이 어떻게 동작하는지, HTTP 통신을 위해 사용하는 메시지의 형식이라던지, HTTP 기저의 TCP 네트워크 전송이라던지, 여러 종류의 HTTP 프로토콜이라던지, 여러 곳곳에 설치된 다양한 HTTP 구성요소라던지에 대한 궁금증을 개략적으로 결할 수 있을 것이다.

<br>

## 1.1 HTTP : 인터넷의 멀티미디어 배달부

- HTTP는 jpeg이미지, html페이지, 동영상 파일, 음성 파일 등을 웹 서버로부터 빠르고, 간편하고, 정확하게 사람들의 pc에 설치된 웹 브라우저로 옮겨준다.

- 신뢰성이 있는 데이터 전송 프로토콜을 사용하여 전송 중 손상되거나 꼬이지 않음을 보장해준다. 이는 사용자에게도 안전한 통신을 보장지만 개발자도 인터넷의 결함이나 약점에 대한 걱정 없이 애플리케이션의 고유의 기능을 구현하는데 집중할 수 있게해준다.

<br>

## 1.2 웹 클라이언트와 서버

- HTTP 프로토콜로 의사소통을 하는 웹 서버를 보통 `HTTP 서버`라고 부른다.

- HTTP 클라이언트와 HTTP 서버는 월드 와이드 웹(WWW)의 기본 요소

- 웹 서버 (HTTP 서버)

  - 인터넷의 데이터(웹 콘텐츠)를 저장
  - HTTP 클라이언트가 요청한 데이터를 제공

- 웹 클라이언트

  - 서버에게 필요한 데이터를 HTTP 요청을 보냄.
  - 가장 흔한 클라이언트로는 인터넷 익스플로러, 크롬 같은 웹브라우저이다.

  ```
  웹브라우저 : 서버에게 HTTP 객체를 요청하고 사용자의 화면에 보여준다.
  ```

<br>

<center><img width="641" alt="client-server" src="https://user-images.githubusercontent.com/37801041/73855822-f5c72a80-4877-11ea-8e29-0a57e17f83c9.png"></center>

> 위의 그림은 클라이언트가  `http://www.hooong.com/index.html`주소로 페이지를 열려고 하는 상황이다. 웹브라우저는 HTTP 요청(request)을 `www.hooong.com` 이라는 서버로 보내고, 서버는 이 요청에서 찾는 'index.html' 객체를 서버 안에서 찾고, 찾는데 성공을 했다면 그것의 타입, 길이 등의 정보와 함께 HTTP 응답(response)에 실어 클라이언트에게 보내주고 클라이언트(즉, 웹브라우저)는 이를 렌더링하여 사용자에게 보여주게 된다.

<br>

## 1.3 리소스

- `웹 리소스` == `웹 콘텐츠의 원천`

- 웹 서버는 웹 리소스를 관리하고 제공한다.

  ```
  - 정적파일 : 텍스트 파일, HTML 파일, 워드 파일, JPEG 이미지, AVI 동영상 파일 등 모든 종류의 파일
  - 동적 콘텐츠 리소스 : 요청에 따라 콘텐츠를 생산하는 프로그램도 리소스가 될 수 있다. 즉, 사용자가 누구인지, 어떤 정보를 요청했는지, 몃 시인지에 따라 다른 콘텐츠를 생성 (라이브 영상, 주식거래 등)
  ```

- 따라서 어떤 종류의 컨텐츠 소스도 리소스가 될 수 있다. => 가령 기업 판매 예측 스프레드시트 파일도 리소스이고, 인터넷의 웹 검색엔진 역시 리소스이다.

  <br>

### 1.3.1 미디어 타입

- 수천 가지의 데이터 타입을 효율적으로 다루기 위하여 MIME (Multipurpose Internet Mail Extensions) 타입이라는 데이터 포맷 라벨을 붙임.

- 원래는 각기 다른 전자메일 시스템 사이에서 메시지가 오갈 때 겪는 문제점을 해결하기 위해 설계되었지만 이메일에서 워낙 작동을 잘해서 HTTP에서도 멀티미디어 콘텐츠를 기술하고 라벨을 붙이기 위해 체택되었다고 함.

- 웹브라우저는 서버로부터 응답을 받고 다룰 수 있는 객체인지 MIME 타입을 통해 확인.

- MIME 타입은 사선(/)으로 구분되며 주 타입(primary object type)와 부 타입(specific subtype)으로 이루어진 문자열 라벨.

  ```
  * JPEG 이미지
  Content-type: image/jpeg       
  
  * HTML 파일
  Content-type: text/html
  
  * plain ASCII 텍스트 문서
  Content-type: text/plain
  
  * json포맷의 파일
  Content-type: application/json
  
  * mp3 파일
  Content-type: audio/mpeg
  ```

  - 참고 : [https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Complete_list_of_MIME_types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Complete_list_of_MIME_types)

