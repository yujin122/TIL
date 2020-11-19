# Cookie & Session
<br><br>

## Cookie
사용자가 웹 사이트를 처음 방문할 때 웹 사이트에서 `클라이언트의 컴퓨터에 저장`해 놓은 파일

- http 프로토콜의 웹 브라우저에 응답 후 일정 시간이 지나면 접속을 끊는 특징때문에 사용
<br>

### 특징

- 서버에서 생성, 클라이언트 컴퓨터에 저장

- 웹 브라우저가 관리
- 4KB 크기로 제한, 300개 정도의 쿠키를 만들어 사용 가능
- `보안에 취약`
<br>

### 생성
1. 쿠키 클래스 사용

	    Cookie cookie = new Cookie(key, value)


		cookie.setMaxAge(60*30);

3. 쿠키 전송

		response.addCookie(cookie);
<br>

### 메서드

- ***setMaxAge()*** : 쿠키의 `유효 기간`을 설정하는 메서드

- ***setPath()*** : 쿠키 사용을 위한 `디렉토리`를 설정하는 메서드 (특정 경로명을 갖는 url로 전송하도록 설정)
- ***setValue()*** : `쿠키값`을 설정하는 메서드
- ***setVersion()*** : `쿠키의 버전`을 설정하는 메서드
- ***getMaxAge()*** : 쿠키의 `유효기간` 정보를 얻어오는 메서드
- ***getName()*** : 쿠키의 `이름`을 얻어올 때 사용하는 메서드
- ***getPath()*** : 쿠키의 유효 `디렉토리 정보`를 얻어올 때 사용하는 메서드
- ***getVersion()*** : 쿠키의 `버전`을 얻어올 때 사용하는 메서드
- ***getCookies()*** : 쿠키 `데이터`를 읽어올 떄 사용하는 메서드 <br>
  					 => 웹 브라우저가 보낸 쿠키를 `배열`로 반환해 주는 메서드.
<br>

### 사용 순서
1. 웹브라우저에 요청을하여 쿠키를 얻어옴

		request.getCookies();

2. 이름, 값의 쌍으로 된 배열 형태로 반환

		Cookie[] cookies = request.getCookies();

3. 반환된 쿠키의 배열에서 쿠키의 이름을 가져옴

		cookies[i].getName();

4. 쿠키의 이름을 통해 쿠키의 설정된 값을 추출

		cookies[i].getValue()

<br>

## Session
서버와의 connection 관계를 유지하기 위해 이용자 정보를 `서버에 저장`하는 객체
<br>

### 특징
- 서버에서만 접근 가능

- `보안성이 높음`
- 서버에 부하를 줌
- 데이터 제한이 없음
- 유효 시간을 가짐(기본 30분)
<br>

### 메서드
- ***setAttribute()*** : 세션의 `속성을 설정`하는 메서드 <br>
			
		session.setAttribute("id", value);
			 
- ***getAttribute()*** : 세션에서 `데이터`를 얻어올 때 (세션에 속성을 사용할 때) 이용하는 메서드<br>

		String id = (String)session.getAttribute("id");

- ***getAttributeNames()*** : 세션에 저장되어 있는 모든 `데이터의 이름`을 얻어올 때 사용하는 메서드
- ***removeAttribute()*** : 세션의 `특정 데이터를 제거`하는 메서드<br>

		session.removeAttribute("id");

- ***invalidate()*** : 세션의 `모든 데이터를 삭제`하는 메서드.
- ***getId()*** : 자동 생성된 `세션의 아이디`를 얻어올 때 사용하는 메서드.
- ***isNew()*** : 세션이 최초로 생성되었는지 여부를 알고자 할 때 사용하는 메서드.
- ***getMaxInactiveInterval()*** : 세션의 `유효 시간`을 얻었을 때 사용하는 메서드.
<br>

### 사용 순서

1. 세션 설정

		session.setAttribute(key1, value1)
		session.setAttribute(key2, value2)

2. 세션 사용

		session.getAttribute(key1)
		session.getAttribute(key2)
