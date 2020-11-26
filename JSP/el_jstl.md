# EL(Expression Language)

자바 코드가 들어가는 표현식(<%  %>, <%=  %>)을 좀 더 편리하게 사용하는 데이터 출력 기능
<br>

### 특징
- 기존의 표현식보다 편리하게 값을 출력
- 변수와 여러 가지 연산자를 포함
- 내장 객체 지원
<br>

### 형식

    <%=변수 %> ⇒ ${변수(수식) }
<br>

### 내장객체
- ***pageScope*** : 현재 페이지의 범위에만 한정, 페이지가 끝나면 유효하지 않게 된다.

- ***requestScope*** : request 생명 주기는 request 요청을 받고, 요청에 대한 처리를 완료하는 시점
- ***sessionScope*** : session의 생명 주기는 설정된 유효시간이 기준이 된다.
- ***applicationScope*** : 웹 사이트가 실행되는 동안만 유효하게 된다.
- ***param*** : 파라미터 값을 얻어올 때 사용
- ***paramValues*** : 파라미터 값을 배열로 얻어올 때 사용
<br>

# JSTL(JSP Standard Tag Library)
JSP 페이지에서 스크립트릿에 들어가는 자바 코드 중에 논리적인 판단, 반복처리, 포맷 처리 등을 HTML 태그처럼 처리할 수 있도록 표준으로 만들어서 정의한 라이브러리

### JSTL 태그
출력은 EL 사용

1. 변수 태그

	    <c:set var = "변수명" value = "값" />

3. 출력 태그

		<c:out value = "변수명" />

4. 삭제 태그

		<c:remove var = "변수명" />

5. 조건 처리 태그

		<c:if test = "조건식" var = "변수명"></c:if>

6. 조건 처리 태그

		 <c:choose>
				      <c:when test = "조건식1"> 조건식1이 참인 경우 실행문장 </c:when>
				      <c:when test = "조건식2"> 조건식2이 참인 경우 실행문장 </c:when>
				      <c:when test = "조건식3"> 조건식3이 참인 경우 실행문장 </c:when>
				      <c:when test = "조건식4"> 조건식4이 참인 경우 실행문장 </c:when>
				      <c:otherwise>상기 조건식 이외의 경우 실행문장 </c:otherwise>
		</c:choose>

7. 반복문 태그

		<c:forEach begin = "시작값 end = "끝값" step = "증감값" var = "변수명">
		</c:forEach>

		<c:forEach items = "객체명" var = "변수명">
		</c:forEach>
