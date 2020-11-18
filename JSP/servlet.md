# Servlet
서버 쪽에서 실행되면서 클라이언트의 요청에 따라 `동적으로 서비스를 제공`하는 자바 클래스

- 서버에서 실행되기 때문에 보안과 관련된 기능도 훨씬 안전하게 수행이 가능

- 서블릿은 서버에서 실행되다가 웹 브라우저에서 요청을 하면 해당 기능을 수행한 후에 웹 브라우저에 결과를 전송.
<br>

## Servlet Life Cycle(서블릿 생명 주기)

1. ***init()*** : 서블릿이 서비스하기 위해 필요한 `초기화 작업`을 수행, 단 한번만 호출
2. ***service()*** : 사용자의 요청에 따라 `스레드 단위로 실행`되는 메서드
3. ***destroy()*** : `서블릿이 종료`되면서 정리할 작업이 있으면 destroy() 메서드를 오버라이딩, 단 한 번만 호출
<br>

## Servlet 동작 과정

1. 클라이언트가 요청을 하면 요청하는 서블릿이 메모리에 로딩 되어있는지 확인

2. **최초** 요청일 시 `init() 메서드 호출`, 요청하는 클래스의 인스턴스를 메모리에 로딩
3. ***doGet()*** 또는 ***doPost()*** 메서드를 호출하여 수행
4. 클라이언트가 다시 동일한 서블릿을 요청 시 톰캣은 요청하는 서블릿이 메모리에 로딩 되어있는지 확인
5. 메모리에 로딩 되어있는 것을 확인 후 doGet() 또는 doPost() 메서드 호출
<br>

## doGet() / doPost()

**클라이언트의 요청을 처리**하는 메서드

    doGet(HttpServletRequest request, HttpServletResponse response)
    doPost(HttpServletRequest request, HttpServletResponse response)

- **request**, 첫번째 매개변수 : 사용자의 요청에 대한 정보를 처리

- **response**, 두번째 매개변수 : 요청 정보에 대한 처리 결과를 클라이언트에 응답 처리
- javax.servlet.**HttpServletRequest**  : 요청과 관련된 API
- javax.servlet.**HttpServletResponse** : 응답과 관련된 API
<br>

### 메서드

#### HttpServletRequest request

- ***getParameter***(String name) : <form> 태그의 name 속성에 들어간 변수명을 받아서 데이터를 받아옴

- ***getParameterValues***(String name) : <form> 태그의 같은 name 속성에 대해 여러 개의 데이터를 배열로 받아옴
- ***setCharacterEncoding***("utf-8") : 한글 처리
<br>
    
#### HttpServletResponse

- ***setContentType***("text/html; charset=UTF-8") : 응답 시 한글 처리

- ***getWriter()***
<br>

### get / post 방식

< form > 태그에서 `method = "get"` 인 경우 **doGet()** 호출 `method = "post`"인 경우 **doPost()** 호출

1. **get 방식**

- 서블릿에 데이터를 전송할 때 데이터가 `url 뒤에 name = value 형태`로 전송

- 여러 개의 데이터를 전송할 경우 '&'로 구분
- 보안에 취약
- 전송할 수 있는 데이터는 최대 255자

2. **post 방식**
- 서블릿에 데이터를 전송할 때 TCP/IP 프로토콜 데이터의 `head 영역에 숨겨져서 전송`

- 보안에 유리
- 전송 데이터의 용량이 무제한
- 처리속도가 get 보다 느림
