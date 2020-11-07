# 자바스크립트(JavaScript)
- [자바스크립트란?](https://github.com/yujin122/TIL/blob/master/JavaScript/js.md#자바스크립트)
- [데이터 출력 방법](https://github.com/yujin122/TIL/blob/master/JavaScript/js.md#데이터-출력-방법)
- [입력 대화상자](https://github.com/yujin122/TIL/blob/master/JavaScript/js.md#입력-대화상자)
- [변수](https://github.com/yujin122/TIL/blob/master/JavaScript/js.md#변수)
- [관계 연산자](https://github.com/yujin122/TIL/blob/master/JavaScript/js.md#관계-연산자)
- [제어문](https://github.com/yujin122/TIL/blob/master/JavaScript/js.md#제어문)
- [배열(Array)](https://github.com/yujin122/TIL/blob/master/JavaScript/js.md#배열array)
- [함수(Function)](https://github.com/yujin122/TIL/blob/master/JavaScript/js.md#함수function)
- [BOM(Browser Object Model)](https://github.com/yujin122/TIL/blob/master/JavaScript/js.md#BOMbrowser-object-model)
<br>

## 자바스크립트
개발자가 만든 문서에 방문자가 방문하여 어떤 동작을 취했을 때, 그 동작에 대응하여 반응이일어날 수 있도록 해주는 언어. <br>
웹 브라우저에서 사용하기 위해 만들어진 프로그램
<br>

### 특징
1. 자바스크립트는 `인터프리터 언어`
- 코드가 작성된 순서대로 윗줄부터 순차적으로 구문을 분석하여 실행
- 코드에 문제가 생기면 에러가 발생한 행 이전까지만 구문을 분석하여 실행하고, 에러가 발생한 다음 줄 부터는 구문을 분석하지 않음
2. 자바스크립트는 클라이언트 스크립트 언어
- 자바스크립트는 서버에서 실행되는 것이 아니라, 사용자 컴퓨터에서 실행이 된다. 따라서 서버의 부하를 줄여줄 수 있다.
3. `객체 기반 언어`
4. 공개된 언어
5. 다양한 라이브러리를 활용할 수 있다.
- 자바스크립트의 대표적인 라이브러리 언어는 제이쿼리(JQuery)
- 다양한 기능들을 쉽게 구현할 수 있도록 만들어 놓은 함수들의 집합을 이용하면 쉽게 구현이 가능하다. 
<br>

## 데이터 출력 방법

1. ***console.log()*** : 콘솔창에 출력
2. ***document.write()*** : 본문에 출력
<br>

## 입력 대화상자

1. ***alert*** : 알림(경고) 창 

		window.alert("알림내용 또는 경고내용");
		alert("알림내용 또는 경고내용");
2. ***confirm*** : [확인] - (true) / [취소] - (false) 반환

		window.confirm("문자열");
		confirm("문자열");
3. ***prompt*** : 키보드로부터 데이터를 입력받는 방법

		window.prompt("문자열", 초기 값);
		prompt("문자열", 초기 값);
<br>

## 변수

### 변수
데이터를 저장하는 공간. 데이터가 `변할 수 있음`.

    var 변수명;

### 상수 
데이터를 저장하는 공간. 데이터가 `변할 수 없음`.

    const 상수명;
<br>

### 자료형

- 숫자형(***number***) : 숫자를 표현하는 자료형.

- 문자형(***string***) : 작은 따옴표 또는 큰 따옴표 안에 한 글자 이상의 기호 또는 숫자가 있는 자료형
- 불린형(***boolean***) : 참(true) 또는 거짓(false) 두 가지 값을 가지는 자료형
- typeof 연산자 : 해당 변수의 자료형을 알려주는 연산자
- ***null***  : 비어 있는 값
- ***undefined*** : 존재하지 않는 값-
- ***NaN(Not A Number)*** :  숫자가 아닌 데이터를 숫자처럼 사용할 때 나타남.
<br>

## 관계 연산자
결과는 항상 `boolean형`으로 나온다.

>=, >, ==, <, <=, !=, ===

<br>

**==**  <br>
동등연산자로 비교 대상 값의 자료형이 다른 경우 `강제로 형을 바꾼 뒤에 비교`

**===** <br>
`값과 자료형 모두가 일치`할 때 true 값 반환
<br>
<br>

## 제어문

1. **조건문**
- if
- if ~ else
- 다중 if ~ else
- switch ~ case 

2. **반복문** 
- while
- do ~ while
- for
<br>

## 배열(Array)

### 생성 방법
1

    var 배열명 = new Array(원소1, 원소2, 원소3, ...원소n);

2

    var 배열명 = [원소1, 원소2, 원소3, ...원소n];

3 

    var 배열명 = new Array();

##### 자바스크립트에서의 배열은 모든 데이터 타입(자료형)을 다 담을 수 있음.
<br>

### 메서드

- ***push***(요소) : 맨 뒤에 요소 추가
- ***concat***([요소1, 요소2, ...요소n]) : 복수개의 데이터 추가
- ***unshift***(추가할 요소) : 배열의 맨 앞에 추가
- ***shift***() : 맨 처음 요소 제거
- ***pop***() : 맨 마지막 요소 제거
- ***sort***() : 배열의 요소 정렬
- ***reverse***() : 배열의 요소 역순으로 정렬
<br>

## 함수(Function)
`기능을 정의`해 놓은 것

### 종류
1. **사용자 정의 함수** :  사용자가 직접 만들어 놓은 함수.

		function 함수명(인자1, 인자2){
			함수 호출 시 실행 될 문장;
			return 반환값;
		}
		
2. **내장 함수** : 자바스크립트에서 자체적으로 제공해 주는 함수. <br>

**날짜(Date)**
	
		var date = New Date();

**메서드**
- ***getYear***() : 1900년을 기준으로 값을 반환 - 0이라고 인식
- ***getFullYear***() | ***getMonth***() | ***getDate***() : 현재 날짜(년 | 월 | 일)
- ***getDay***() : 현재 요일, 0(일요일) ~ 6(토요일)
- ***getHours***() | ***getMinutes***() | ***getSeconds***() : 현재 시간(시 | 분 | 초)
<br>

**수학(Math)**

- ***abs***(숫자) : 숫자의 절대값을 반환
- ***max***(숫자1, 숫자2, 숫자3, ...숫자n) : 숫자 중 가장 큰 값을 반환
- ***min***(숫자1, 숫자2, 숫자3, ...숫자n) : 숫자 중 가장 작은 값을 반환
- ***pow***(숫자, 제곱값) : 숫자의 거듭제곱한 값을 반환
- ***random***() : 0 ~ 1 사이의 난수를 반환
- ***round***(숫자) : 소수점 첫째 자리에서 반올림하여 정수를 반환
- ***ceil***(숫자) : 소수점 첫째 자리에서 무조건 올림해서 정수를 반환
- ***floor***(숫자) : 소수점 첫째 자리에서 무조건 내림해서 정수를 반환
- ***sqrt***(숫자) : 숫자의 제곱근 값을 반환

<br>

## BOM(Browser Object Model)
`브라우저 객체 모델`, 브라우저 내에 내장된 객체
<br>

### window 객체의 주요 메서드

- ***open***() : 새로운 창을 띄울 때 사용
- ***alert***() : 경고 창을 띄울 때 사용
- ***prompt***() : 질의/응답 창을 띄울 때 사용
- ***confirm***() : 확인/취소 창을 띄울 때 사용
- ***moveTo***() : 창의 위치를 이동시킬 때 사용
- ***resizeTo***() : 창의 크기를 변경시킬 때 사용
- ***setInterval***() : 일정 간격으로 지속적으로 실행문을 실행시킬 때 사용
- ***setTimeout***() : 일정 간격으로 한번만 실행문을 실행시킬 때 사용
<br>

 ### screen 객체
 사용자의 `모니터 정보를 제공`해 주는 객체

- screen.***widht*** : 화면의 너비값을 반환
- screen.***height*** : 화면의 높이값을 반환
- screen.***availWidth*** : 작업표시줄을 제외한 화면의 너비값을 반환
- screen.***availHeight*** : 작업표시줄을 제외한 화면의 높이값을 반환
- screen.***colorDepth*** : 사용자 모니터가 표현 가능한 컬러 bit를 반환
<br>

### location 객체
실행되고 있는 현재 브라우저의 주소창에 표시된 `주소 값에 관련된 내용`을 다루는 객체

- location.***href*** : 브라우저 창의 url 값을 반환
- location.***reload***() : 브라우저 창의 새로고침이 일어나는 메서드
<br>

### history 객체
브라우저가 `페이지를 변경한 이력이 저장`되어 있는 객체

- history.***back***() : 이전에 방문한 페이지로 이동
- history.***forward***() : 다음에 방문한 페이지로 이동
- history.***go***(숫자) : 숫자만틈 페이지로 이동
- ***length*** : 방문 기록에 저장된 목록의 갯수를 반환
