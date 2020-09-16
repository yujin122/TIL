# 메서드(method)
특정 작업을 수행하는 일련의 문장들을 하나로 묶은 것

- 하나의 기능만을 정의하는 것이 좋음
- 자주 반복되는 내용을 정의해 놓고, 필요 시 호출하여 사용

### 사용하는 이유

>  높은 재사용성
>  
>  중복코드 제거
>  
>  프로그램의 구조화

## 형식

    [접근제한] 변환명 메서드이름 (매개변수 또는 인자){ 	
	    메서드 호출 시 실행될 문장; 
    }
```java
public int add (int a, int b){
	return (a+b);
}
```

### 접근제한
public > protected > default > private (클래스, 메서드, 변수 앞에 사용된다)

	public : 아무나 접근 가능.
	
	protected : 같은 패키지 접근 가능, 상속 관계의 경우 다른 패키지도 접근 가능.
	
	default : 같은 패키지에서만 접근 가능, 상속 관계라도 접근 불가.
	
	private : 외부에서 접근 불가.

### 반환형
메서드의 작업 수행 결과인 `반환값(return value)의 타입`을 적는다.
- 생략불가
- 결과를 되돌려 줄 필요가 없는 경우 void 라는 키워드를 사용

### 매개변수 
	[접근제한] 반환형 메서드이름(type 변수1, type 변수2, ...) {
		 메서드 호출 시 실행문;
	  }
  
- 외부에서 값을 넘겨 받는 변수, 생략 가능.
- 메서드 호출 시 전달되는 값의 저장을 위한 용도로 사용
- 메서드 호출 시 전달되는 값의 자료형과 매개변수의 자료형은 반드시 일치해야 한다.

#### 실인수와 가인수
**실인수** : 매개변수에 전달할 실제 값 -> 메서드를 호출할 때 사용
**가인수**  : 매개변수 -> 메서드에 정의
- 실인수와 가인수는 반드시 type, 순서, 갯수가 일치해야 한다.

```java
public static void tot(int su) {	// su --> 가인수	
		System.out.println("x >>> " + su); 
}
public static void main(String[] args) {
	tot(150); // 150 --> 실인수
}
```

## 메서드 호출 방식
### 1. call by value
- 값을 전달하여 호출하는 방식
- 매개변수가 기본자료형(int, float, ...) 사용

```java
public static void call(int x) {
	System.out.println("call() 메서드 호출...");
	x = 100; 
}

public static void main(String[] args) {
	
	// call by value
	int num = 200;
	System.out.println("메서드 호출 전...");	
	System.out.println("num >>> " + num);	//	num >>> 200
	
	call(num);
	System.out.println("메서드 호출 후...");
	System.out.println("num >>> " + num);	//	num >>> 100(X)
}
```
- call 메서드 안에서만 바뀌고 main 메서드에서는 바뀌지 않는다.

### 2. call by reference
- 주소 값을 전달하여 호출하는 방식
- 매개변수 참조자료형(배열명, 클래스명) 사용
 
<img src="https://user-images.githubusercontent.com/46274903/93309667-c1b8dc80-f83e-11ea-99ce-986d8d44fa4b.PNG " width="600"  height="">

- 주소 값을 전달하기 때문에 arr과 a는 같은 배열을 가리키게 된다. 즉, 메소드에서 배열 값을 바꾸면 main 메소드에서도 배열 값이 바뀐다.

```java
public static void change(int[] a) {	// a = [I@6477463f
	System.out.println(a);
	a[0] = 100;
	a[1] = 200;
	a[2] = 300;
} 
	
public static void main(String[] args) {
	// call by reference
	int[] arr = new int[3];
	arr[0]=10; arr[1]=20; arr[2]=30;
	
	System.out.println(arr);
	System.out.println("change() 메서드 호출 전...");
	
	for(int i=0;i<arr.length;i++) {
		System.out.println("arr["+i+"] >>> "+arr[i]);
	}
	System.out.println();
	
	change(arr);
	
	System.out.println("change() 메서드 호출 후...");
	
	for(int i=0;i<arr.length;i++) {
		System.out.println("arr["+i+"] >>> "+arr[i]);
	}
	System.out.println();
}
```
## 메서드 다중정의(method overloading)
동일한 클래스에서 `동일한 이름`의 메서드가 `여러 개 정의`되는 자바 문법

- 일관된 메서드 이름을 정의할 수 있어서 개발자(사용자)에게 코드의 직관성을 제공한다.

### 다중정의규칙

- 메서드 이름이 동일해야 한다.
- 반드시 매개변수는 자료형이 다르거나 순서가 다르거나 또는 매개변수의 갯수가 달라야한다.
- 리턴타입(반환형)은 무관하다.

```java
public static int sum(int k, int e) {
	return k+e;
}
	
public static int sum(int k, int e, int m) {
	return k+e+m;
}
	
public static int sum(int k, int e, int m, int j) {
	return k+e+m+j;
}
```
