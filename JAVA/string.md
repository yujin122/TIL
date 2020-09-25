# String 클래스
문자열 객체를 처리하는 클래스

### 객체 생성 방법
1. 일반 변수 선언 방법으로 객체 생성
```java
String str = "abc";
```
2. new 키워드를 이용하는 방법
```java
String str = new String("abc");
```

### 관련 메서드

- **equals()** : 객체의 내용(데이터)을 대상으로 비교하여 객체가 같으면 true, 다르면 false 값을 반환
```java
if(str.equals(str2)){		}
```
- **toUpperCase()** / **toLowerCase()** : 소문자를 대문자로, 대문자를 소문자로 바꿔주는 메서드

- **length()** : 문자열의 길이를 정수 값으로 반환하는 메서드
- **concat()** : 문자열을 결합하는 메서드
```java
String str1 = "JAVA ";
String str2 = str1.concat("PROGRAM");
```
- **equalsIgnoreCase()** : 대소문자를 구분하지 않고 객체의 내용(데이터)을 비교
```java
if(str.equalsIgnoreCase(str2)) {		}
```
- **charAt(index)** : 문자열에서 특정 단일 문자를 추출하는 메서드
```java
String id = "123456-2345678";
char gender = id.charAt(7);
```

### 단점

> 빈번한 문자열 연산을 실행할 경우 메모리(heap)를 많이 차지 하게 된다.
> 
> 매번 연산 시마다 새로운 객체 생성

# StringBuffer 클래스
String 클래스의 단점을 개선한 클래스

### 관련 메서드
 - **append()** : 문자열을 추가하는 메서드
```java
StringBuffer sb = new StringBuffer("java");

sb.append(" program");
```
 - **replace()** : 문자열을 교체하는 메서드 
 ```java
 // replace(시작 index, 끝 index, "교체할 문자열")
 sb.replace(0, 4, "spring");
 ```
 - **substring()** : 문자열을 추출하는 메서드
	- substring(시작 index, 끝 index)
	 - substring(시작 index)
```java
StringBuffer sb1 = new StringBuffer("2020/09/25 14:22:13");

System.out.println("오늘 날짜 : " + sb1.substring(0, 10));
System.out.println("현재 시간 : " + sb1.substring(11));
```
# StringToTokenizer 클래스
특수문자를 기준문자(delimiter)로 문자열을 잘라 주는 클래스(파싱)

- 기준문자로 분리된 문자열을 토큰(token)이라고 한다.
```java
String query = "id=hong&pwd=1234&age=27";
StringTokenizer st = new StringTokenizer(query,"&");
		
int count = st.countTokens();
		
System.out.println("토큰 수 : " + count);

//hasMoreTokens() : 리턴할 다음 토큰이 있는지 학인
//					있으면 true 없으면 false 값 반환
while(st.hasMoreTokens()) {
	System.out.println(st.nextToken());
}
```
