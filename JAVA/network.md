# 네트워크(Network)
여러 대의 컴퓨터를 통신 회선으로 연결한 것

- 홈 네트워크 : 컴퓨터가 방마다 있고, 이를 컴퓨터를 유선, 무선 등의 통신 회선을 연결
- 지역 네트워크 : 회사, 건물, 특정 영역에 존재하는 컴퓨터를 통신 회선으로 연결
- 인터넷 : 지역 네트워크를 통신 회선으로 연결

## 네트워킹(Networking)
두 대 이상의 컴퓨터를 케이블로 연결하여 네트워크를 구성하는 것

## 클라이언트(Client) / 서버(Server)
### 서버(Server)
서비스를 `제공`하는 컴퓨터

> ex) 웹 서버, FTP 서버, DBMS, 메신저 서버

- 클라이언트의 요청(연결)을 수락하고,  작업을 처리 후 그 결과를 보내는 역할

### 클라이언트(Client)
서비스를 `사용`하는 컴퓨터

> ex) 웹 브라우저, FTP 클라이언트, 메신저

<br/>

- 서비스를 제공하기 위해서는 `서버프로그램`이 있어야 하고 서비스를 제공받기 위해서는 서버프로그램과 연결할 수 있는 `클라이언트 프로그램`이 있어야 한다.
	- **서버기반모델**(server-based model) : 네트워크를 구성할 때 전용서버를 두는 것

	- **P2P**(peer-to-peer model) : 전용서버 없이 각 클라이언트가 서버역할을 동시에 수행하는 것
<br/>

### IP주소와 포트
#### IP(Internet Protocol) 주소
컴퓨터를 `구별`하는데 사용되는 `고유한 값`

- 모든 컴퓨터는 IP주소를 갖는다.
- 4byte의 정수로 구성 (형식 : a.b.c.d  /  a,b,c,d 는0~255 사이의 정수)

#### InetAddress
IP주소를 다루기 위한 클래스

- *InetAddress* **getLocalHost**() : 지역호스트의 IP주소 반환 
- 내 컴퓨터의 IP 주소 : **getHostAddress**() 사용
```java
InetAddress local = InetAddress.getLocalHost();
System.out.println("내 컴퓨터 IP 주소 : " + local.getHostAddress());
```

#### 포트(port)
같은 컴퓨터 내에서 `프로그램을 식별`하는 번호
<br/>

### 소켓
`프로세스간의 통신에 사용`되는 양쪽 끝단
<br/>

#### TCP / UDP

|  | TCP| UDP	|
|--|--|--|
|연결방식 | **연결기반** <br/> 연결 후  통신 |**비연결기반** <br/> 연결없이 통신 	|
|특징 |**신뢰성 있는 데이터 전송** <br/> - 전송순서 보장 <br/> - 수신여부 확인 <br/> UDP보다 전송속도가 느림 |**신뢰성 없는 데이터 전송** <br/>	- 전송 순서가 바뀔 수 있음 <br/> - 수신여부 확인 X <br/> TCP보다 전송속도가 빠름|
 <br/>
 
<img src="https://user-images.githubusercontent.com/46274903/95432304-726f5300-0989-11eb-98e4-6eefe13d21e6.PNG " width=""  height="">

- **Socket** : 프로세스 간의 통신 담당, InputStream과 OutputStream을 통해 프로세스 간의 통신이 이루어짐
- **ServerSocket** : 포트와 연결(bind)되어 외부의 연결 요청을 기다리다 연결요청이 들어오면, Socket을 생성해서 소켓과 소켓 간의 통신이 이루어지도록 함
<br/>

#### Server
```java
// 서버 소켓 생성
ServerSocket serverSocket = new ServerSocket();
// accept() : 클라이언트의 요청을 받아드림
Socket socket = serverSocket.accept();
// 클라이언트에서 보낸 데이터 받기
InputStream is = socket.getInputStream();
// 클라이언트로 데이터를 보내기
OutputStream os = socket.getOutputStream();
os.write(bytes);
```
<br/>

#### Client
```java
Socket socket = new Socket();
// 서버에게 연결 요청
socket.connect(new InetSocketAddress("localhost",5001));
```
