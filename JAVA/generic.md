# 제네릭(Generic)
특정한 클래스에 원하는 객체 타입을 지정하여 지정된 객체만 저장하게 하는 자바 문법

- 클래스 내부에서 사용할 데이터를 외부에서 지정하는 방법
- 다루어질 객체의 타입을 미리 명시함으로써 형변환을 줄여 준다.
- 데이터의 명확성과 안정성을 보장

```java
class Generic<T>{
	T[] str;
	T var;
	
	void setArr(T[] str) {
		this.str = str;
	}
	
	void setVar(T var) {
		this.var = var;
	}
	
	void prn() {
		for(T k : str) {
			System.out.println("str 배열 요소 : " + k);
		}
		System.out.println("var " + var);
	}
}
```
```java
// Integer 타입의 클래스 작성
Generic<Integer> it = new Generic<Integer>();

Integer[] iarr = {100, 200, 300};
Integer ivar = 500;

it.setArr(iarr);
it.setVar(ivar);
it.prn();
```
```
str 배열 요소 : 100
str 배열 요소 : 200
str 배열 요소 : 300
var 500
```
