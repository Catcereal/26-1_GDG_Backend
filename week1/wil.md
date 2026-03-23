# GDG 백엔드 정규 스터디 1주차
-----------------
# 1. 학습한 내용

- **인터넷**: 전 세계의 컴퓨터와 기기를 연결하는 글로벌 네트워크
- **웹**: 인터넷 위에서 동작하는 서비스 중 하나이다

## 클라이언트 - 서버 모델
웹에서 컴퓨터들이 주고받는 대표적인 방식
- 클라이언트 : 요청(request)을 보내고, 서버의 응답 결과를 받아 사용
- 서버 : 클라이언트의 요청을 받아 처리하고, 그에 대한 응답(response)을 반환
**예)** 내 컴퓨터(클라이언트)에서 내가 홍익대 홈페이지 데이터를 달라고 홍익대 서버 컴퓨터(서버)에 요청을하면,
서버는 그에 대한 응답으로 홍익대 홈페이지 데이터를 준다 (Request - Response)
  
## URL
URL : Uniform Resource Locator 
웹 상에서 특정 자원의 위치를 나타내는 "주소"
- **Host**: 리소스가 위치한 "서버"의 IP 주소 혹은 도메인
- **Port**: 서버의 특정 네트워크 포트번호 (일반적으로 생략한다)
- **Path**: 서버 내에서 원하는 리소스의 경로 (" /category/food.html => 디렉토리 같다 뭔가)
- **Query**: 서버에서 추가적인 정보를 보내는 파라미터로, **?** 뒤에 "key-value" 형식으로 나열한다
- **Scheme**: **Protocol**, 컴퓨터 같은 장치들 사이에서 데이터를 주고 받는 방식; 통신하기 위한 "규칙"
  
## HTTP
HTTP : HyperText Transfer Protocol
웹에서 데이터를 주고받도록 하는 클라이언트-서버 모델의 프로토콜이다
  
**HTTP의 특징**
- 무상태성(Stateless): 서버는 클라의 이전 요청을 저장하지 않는다. 매 요청을 독립적으로 처리한다
- 비연결성(Connectionless): 클라가 요청을 보내고 응답을 받게되면, 서버와 연결을 유지하지 않는다
  
**HTTP 요청**
클라이언트가 보내는 요청의 구조. 크게 **Start Line, Headers, Body**로 구성됨
- **Start Line**: 요청 메서드, 요청할 경로, HTTP 버전 정보를 포함한다
- **Headers**: 요청에 대한 부가적인 정보를 포함
- **Body**: 실제로 전송할 데이터 (예: 우리가 입력한 아이디나 비밀번호 같은 데이터)

**HTTP 주요 메서드**
| 메서드 | 기능 |
|-------|------|
| GET | 리소스를 조회 |
| POST | 리소스를 추가, 등록 |
| PUT | 리소스를 교체, 없으면 새로 생성 |
| PATCH | 리소스의 일부를 수정 |
| DELETE | 리소스를 삭제 |

**HTTP 응답**
서버가 클라이언트한테 보내는 응답의 구조. 크게 **Status Line, Headers, Body**로 구성
- **Status Line**: HTTP 버전, HTTP 상태코드, 상테 메시지를 포함한다.
- **Headers**: 응에 대한 부가적인 정보를 포함
- **Body**: 클라이언트가 요청한 실제 데이터

**HTTP 주요 상태 코드**
| 코드 | 의미 |
|------|-----|
| 200 OK | 요청이 성공적으로 처리됨 |
| 201 Created | 요청이 성공적으로 처리되어 새로운 리소스가 생성됨 |
| 404 Not Found | 지정한 리소스를 찾을 수 없음 |
| 500 Internal Server Error | 서버 내부 오류로 요청을 처리할 수 없음 |
| 400 Bad Request | 클라이언트의 요청이 잘못되어 서버가 이해하지 못함 |

그래서 이제 내 컴퓨터로 홍대 서버에 요청을 보낸다면,  <br>
**GET** http://www.hongik.ac.kr 이라는 경로의 자원을 요청하는 HTTP의 요청 메시지를 만들어 서버에 보낼 것이다. <br>
그리고 요청을 받은 서버 컴퓨터는 요청에 대해서, 정상적으로 처리가 되었다면 <br>
**200 OK** 상태코드와 함께 코드를 바디에 담아서 클라에게 보낼것이다. 메시지를 받은 클라는 이 코드를 통해서, <br>
메인페이지를 불러온다.

그러나 매번 서버에서 HTML 코드 자체를 다 보내주게 되면, 서버에 부하가 발생하며, 불편하다.
<br> -> 그래서 화면의 뼈대는 재사용하고, 필요한 데이터만 서버에서 받아와 부분적으로 다시 그리는 방법이 발전

- **Front-end**: 사용자가 보고 상호작용하는 화면. 사용자 인터페이스(UI)를 개발한다.
- **Back-end**: 요청을 받아 실제 동작을 처리하고, 데이터를 저장하고 관리한다.

<br>서버에서 다루는 데이터는 방대하다. 이 데이터는 **영구적으로, 안전하게, 그리고 효율적으로** 보관이 이뤄져야한다.
<br>이를 위해서 **데이터베이스**를 사용한다. 

## API와 REST API
- **API**(Application Programming Interface): 한 프로그램이 다른 프로그램의 기능이나 데이터를 사용할 수 있도록 미리 정해놓은 약속(규칙)이자 소통 창구
  API란 클라이언트와 서버가 소통할 때 어떻게 요청을 보내고, 어떻게 응답할지 등을 미리 정해놓은 규칙과 기능의 목록이다!
  <br>
- **REST**(Representational State Transfer): REST는 네트워크 아키텍처 스타일로, HTTP의 장점을 최대한 활용할 수 있는 아키텍처
<br>

### REST 구성 요소
1. 자원 (Resource) - URI <br>
  모든 자원은 고유한 ID를 가지며, 이 ID는 /student/1 같은 HTTP URI이다.<br>

2. 행위 (Verb) - Method<br>
  자원을 조작하기 위해 HTTP Method를 사용한다.<br>

3. 표현 (Representation)<br>
  서버와 클라이언트가 데이터를 주고 받는 형식으로, JSON 형식이 일반적이다.<br>
  **JSON**(JavaScript Object Notation): 자바스크립트 객체문법을 기반으로 한 가벼운 데이터 형식<br>

**REST : HTTP를 잘 활용하기 위한 "원칙"**  <br>
**REST API는 이 원칙을 준수해서 만든 API. HTTP의 "모범 사례"**

## 2. Spring Boot 실습환경

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/4c4c1dea-ea2a-4de9-8f81-aac9382209c8" />

## 온라인 쇼핑몰 프로젝트 API 명세서

### 상품 기능
1. 상품 정보 등록<br>
  HTTP Method : POST<br>
  URL : /products<br>
2. 상품 목록 조회<br>
  HTTP Method : GET<br>
  URL : /prducts<br>
3. 개별 상품 정보 상세 조회<br>
  HTTP Method : GET<br>
  URL : /products/{productsID}<br>
4. 상품 정보 수정<br>
  HTTP Method : PATCH<br>
  URL : /products/{productsID}<br>
5. 상품 삭제<br>
  HTTP Method : DELETE<br>
  URL : /products/{productsID}<br>
<br>

### 주문 기능
1. 주문 정보 생성<br>
  HTTP Method : POST<br>
  URL : /orders<br>
2. 주문 목록 조회<br>
  HTTP Method : GET <br>
  URL : /orders<br>
3. 개별 주문 정보 상세 조회<br>
  HTTP Method : GET<br>
  URL : /orders/{ordersID}<br>
4. 주문 취소<br>
  HTTP Method : DELETE<br>
  URL : /orders/{ordersID}<br>
