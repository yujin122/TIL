## 에러(Error)
하드웨어의 오동작 또는 고장으로 인한 오류

- 에러가 발생하면 프로그램 종료.
- 정상 실행 상태로 돌아갈 수 없음.

## 예외(Exception)
사용자의 잘못된 조작 또는 개발자의 잘못된 코딩으로 인한 오류

- 예외가 발생하면 프로그램 종료.
- 예외 처리를 추가해 주면 정상 실행 상태로 돌아갈 수 있음.
- 위험한 상황에서 다른 코드를 보호하는 장치

### 종류
1. 일반(컴파일) 예외
- 예외 처리 코드가 없다면 컴파일이 되지 않는 예외
2. 실행 예외
- 예외 처리 코드를 생략하더라도 컴파일 되는 예외

### 목적

> 프로그램 실행 시 발생할 수 있는 상황들을 미리 정해 놓고, 
>
>예외가 발생했을 경우에 대비하는 코드를 작성하여 
>
>프로그램이 정상적으로 작동하도록 하기 위해서이다.

## 예외 처리
실행 시간에서 발생한 예외(오류)를 프로그램으로 처리한다는 의미

### 1. try ~ catch ~ finally
**형식)**

	try{
	
		예외가 발생할 가능성이 있는 코드;
		
	}catch(예외클래스 참조변수){
	
		예외가 발생 시 실행되는 내용;
		참조변수 : 예외 정보를 넘겨 받는 변수
		
	}finally{
	
		// 생략가능
		예외와 상관없이 실행되는 코드
		
	}

```java
System.out.println("프로그램 시작");
	
int num1 = 10, num2 = 0;
int result = 0;

try {
	result = num1 / num2;	// 0 으로 나눔	
}catch(Exception e){		// 자세한 예외 클래스를 모를 경우 Exception 을 사용
	System.out.println("예외정보 : " + e);
}

System.out.println(result);
System.out.println("프로그램 종료");
```
```
프로그램 시작
예외정보 : java.lang.ArithmeticException: / by zero
0
프로그램 종료
```
#### 다중 catch문
catch문을 여러 개 사용하여 예외를 처리하는 방식

- catch문은 순차적으로 실행
- 예외를 처리하는 가장 상위의 Exception클래스는 맨 마지막 줄에 나와야 한다.

```java
System.out.println("프로그램 시작");
	
Scanner sc = new Scanner(System.in);

int num = 0;

String str = "korea";

int[] arr = {10, 20, 30, 40, 50};

try {
	num = sc.nextInt();
	System.out.println("str 문자열 길이 : " + str.length());
	arr[5] =100;
	
}catch(InputMismatchException e) {
	System.out.println("타입 불일치 오류 발생");
	System.out.println("예외 정보 : " + e);
}catch(NullPointerException e) {
	System.out.println("값이 없는 예외 발생");
	System.out.println("예외 정보 : " + e);
}catch(Exception e) {
	System.out.println("모르는 예외 발생");
	System.out.println("예외 정보 : " + e);
}finally {
	sc.close();
}

System.out.println("num >>> " + num);
System.out.println("프로그램 종료");
}
```

### 2. throws
throws로 지정된 메서드를 호출할 경우 메서드 내에서 예외가 발생이 되면 해당 예외를 메서드를 호출한 곳으로 위임시켜 예외를 처리 

**형식)**

    메서드명 throws 예외처리클래스{		}

```java
public class Ex09 {
	void exception1() throws Exception{
		String str1 = "java";
		String str2 = null;
		
		System.out.println("str1 문자열 길이 : " + str1.length());
		System.out.println("str2 문자열 길이 : " + str2.length());
	}
		
	void exception2() throws Exception{
		int num1 = 15, num2 = 0, result = 0;
			
		result = num1 / num2;
			
		System.out.println("result >>> " + result);
	}
	public static void main(String[] args) {
		Ex09 ex09 = new Ex09();
		
		// 예외 처리
		try {
			ex09.exception1();
		} catch (Exception e) {
			e.printStackTrace();
		}
		try {
			ex09.exception2();
		} catch (Exception e) {
			e.printStackTrace();
		}
	}
}
```
```
str1 문자열 길이 : 4
java.lang.NullPointerException
	at sist.Ex09.exception1(Ex09.java:18)
	at sist.Ex09.main(Ex09.java:34)
java.lang.ArithmeticException: / by zero
	at sist.Ex09.exception2(Ex09.java:25)
	at sist.Ex09.main(Ex09.java:39)
```

