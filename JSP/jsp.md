# JSP
Java Server Page의 약자로 자바 Servlet 기술을 확장시켜 웹 환경에서 자바로 개발하기 위한 기술, <br>
`동적인 페이지를 생성하기 위한 서버 측 스트립트 언어.`

- 서블릿의 비지니스 로직과 결과를 보여주는 화면 기능을 분리
- 개발 후 재사용성과 유지관리가 훨씬 수월해짐
<br>

## 구성 요소

1. ***<%  자바코드  %>*** , 스크립트릿 : `자바 코드를 작성`하고 싶을 때 사용

2. ***<%= 자바코드 %>*** , JSP 표현식 : 변수나 메서드의 `결과 값을 출력`할 때 사용
3. ***<%!	자바코드 %>*** , JSP 선언부 : `변수나 메서드를 선언`할 때 사용
<br>

## 지시어(디렉티브)

JSP페이지에 대한 설정 정보를 지정하는 공간

1. ***<%@ page %>*** : JSP페이지에 대한 정보를 지정하는 공간
- 클라이언트 요청에 JSP 페이지가 실행될 때 필요한 정보를 JSP 컨테이너(톰캣)에 알려주는 역할
<br>

2. ***<%@ include %>*** : 현재 페이지에 다른 문서(JSP, HTML)를 가져와서 내용을 컴파일 할때 사용
#### 형식

	<%@ include file = "포함할 파일의 url" %>

- include 지시어를 사용한 JSP페이지가 컴파일이 되는 과정에서 include 되는 JSP 페이지의 소스 내용을 그대로 포함해서 컴파일을 함.
<br>

3.  ***<%@ taglib %>*** : 사용할 태그 라이브러리 지정
<br>

## JSP 내장 객체
객체를 생성하지 않고 사용할 수 있는 객체

- JSP 페이지가 Servlet으로 변환될 때 JSP 컨테이너가 자동적으로 제공해 줌
<br>

### 종류
1. ***pageContext*** : JSP페이지에 대한 정보를 저장하고 있는 객체

2. ***request*** : 웹 브라우저의 `요청 정보를 저장`하고 있는 객체
3. ***response*** : 웹 브라우저의 요청에 대한 `응답 정보를 저장`하고 있는 객체
4. ***out*** : JSP페이지에 `출력할 내용을 저장`하고 있는 객체
5. ***session*** : 하나의 웹 브라우저의 정보를 유지하기 위한 `세션 정보를 저장`하고 있는 객체
6. ***application*** : 웹 애플리케이션 Context의 정보를 저장하고 있는 객체
<br>

### 메서드

1. ***setAttribute***(String key, Object value) : 주어진 key 속성의 값을 value로 지정

2. ***getAttribute***(String key) : 주어진 key 속성의 값(value)을 얻어냄.
3. ***removeAttribute***(String key) : 주어진 key 속성의 값을 제거
4. ***getAttributeNames***() : 모든 속성의 이름을 구함.
<br>

## JSP 페이지 이동

- 요청에 대한 추가 작업을 `다른 서블릿에게 수행`하게 할 때
- 요청에 포함된 정보를 `다른 서블릿이나 JSP와 공유`할 때
- 요청에 정보를 포함시켜 `다른 서블릿에게 전달`할 때 사용
<br>

### 1. forward 방식
- **주로 키 값을 넘겨줄 때 사용**

- `서블릿이 직접 요청`하는 방식
- 이동된 화면이 url 창에 안보임
- request의 영역에 담긴 값이 유효
- RequestDispatcher 객체 사용

**형식**

    RequestDispatcher rd = request.getRequestDispatcher("이동위치");
    
    rd.forward(request, response);
<br>

### 2. redirect 방식
- **변수 값을 넘겨줄 때 사용**

- `웹 브라우저에 재요청`하는 방식
- 새로 페이지를 요청하는 것과 같은 방식으로 페이지가 이동
- request, response 값이 유효하지 않음
- 이동된 url이 화면에 나타남

**형식**

    response.sendRedirect("이동위치");

