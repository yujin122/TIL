# 객체(Object)란?
실제로 존재하는 것. 책상, 의자, 자동차와 같은 사물들을 객체라고 한다.

- 객체들은 자신만의 고유한 `특성(속성)과 행동(기능)`을 가지고 있다.
- 객체들은 다른 객체들에게 행동을 요청하거나 정보를 주고 받는 등 상호작용을 하며 존재한다.

## 클래스(Class)란?
`객체를 정의`해놓은 것 또는 객체의 설계도(틀, 도면)이다. 객체를 생성할 때 사용

- 클래스를 구성하는 것을 멤버(member)라고 한다.
	- 속성(property) : 멤버변수, 클래스의 특징 
		ex) 크기, 길이, 높이, ...
	- 기능(function) : 멤버메서드, 클래스의 행위(동작)
		ex) 더하기, 곱하기, 검색하기, ...
- 객체를 만드는 과정을 클래스의 `인스턴스화(instantiate)`라고 하고 그렇게 만들어진 객체를 `인스턴스(instance)`라 한다.

### 형식
	[접근제한] class 클래스이름{
			멤버변수;
			생성자();
			멤버메서드;
	}
- 클래스의 이름은 대문자로 시작
```java
public class Class {
	// 멤버변수는 초기값을 설정하지 않으면 JVM이
	// 객체 생성 시점에 해당 테이터 타입(자료형)에 맞게 알아서
	// 해당 자료형의 default 값을 할당해 줌.
	int num;	// 멤버변수 - 전역변수
	String str;	// 멤버변수 
	
	void display() {	// 멤버메서드
		int su = 10;	// 지역변수
		System.out.println("멤버변수(num) >>> " + num);
		System.out.println("멤버변수(str) >>> " + str);
		System.out.println("변수(지역변수) >>> " + su);
	}
}
```

### 구현
1. 클래스 선언 및 클래스 객체 생성


		클래스이름 참조변수 = new 클래스이름()  ==> 생성자
	
	```java
	Class ex = new Class();
	```

2. 참조변수를 이용하여 객체에 접근, 접근 시 .연산자 이용
	```java
	ex.num = 100;
	ex.display();
	```

## 자바에서 사용되는 용어들

1. **변수** : 프로그램이 끝날 때까지 언제든지 변할 수 있는 속성 
2. **상수** : 프로그램이 끝날 때까지 절대 변하지 않는 속성
3. **인스턴스(instance) 변수/메서드**
- 객체의 생성과 동시에 만들어지는 변수/메서드
- 객체는 `heap 메모리 공간`에 만들어짐
- 반드시 `객체 생성 후 사용`이 가능
- 호출방법 : 참조변수.멤버변수 or 참조변수.멤버메서드
4. **static(스태틱, 정적) 변수/메서드**
- 객체의 생성과 상관없이 별도로 만들어지는 변수
- `static 메모리(method 영역)`에서 별도로 만들어짐
- `객체를 생성하지 않아도` 어느 클래스나 접근 가능
- 항상 메모리에 상주하게 되어 메모리 회수가 안되는 단점이 있음
- 호출방법 : 클래스이름.멤버변수 or 클래스이름.멤버메서드
5. **지역변수(local variable)**
- 메서드 블럭 안에서 선언된 변수
- 메서드 블럭이 끝나는 순간 생명이 끝남

### 클래스 메서드(static메서드)와 인스턴스(instance) 메서드

- 클래스 메서드(static메서드)는 인스턴스 변수를 사용할 수 없다.
	-> 클래스 메서드는 항상 메모리에 존재하지만 인스턴스 변수는 인스턴스를 생성해야만 존재한다.
	-> 클래스 메서드가 호출되었을 때 인스턴스가 존재하지 않을 수 있다.
- 메서드 내에서 인스턴스 변수를 사용하지 않는다면, static을 붙이는 것을 고려한다.
	-> 메서드 호출시간이 짧아 성능이 향상된다.
```java
class Add {
	
	// 멤버변수
	int su1 = 200;	// 인스턴스 변수
	int su2 = 100;	// 인스턴스 변수
	static int num = 500;	// static(정적) 변수
	
	// 멤버메서드
	public void sum() {		// 인스턴스 메서드
		System.out.println("sum >>> " + (su1 + su2));
	}
	
	// static 메서드
	public static int adder(int num1, int num2) {
		return num1 + num2;
	}	
}

public static void main(String[] args) {
		
	System.out.println(Add.num);
	System.out.println("adder() 메서드 호출 결과 >>> "+ Add.adder(150, 36));
	
	// 인스턴스 변수이기 때문에 error 발생
	// System.out.println(Add.su1); => error
		
	// 인스턴스 변수는 반드시 객체 생성(new) 후 사용이 가능함
	Add add01 = new Add();
	System.out.println(add01.su1);
	System.out.println(add01.su2);
	ex01.sum();
}
```
## 생성자(Constructor)
인스턴스가 생성될 때 호출되는 '`인스턴스 초기화 메서드`'

- 인스턴스 변수의 초기화 작업에 주로 사용되고 인스턴스 생성 시 실행되어야 할 작업을 위해서도 사용
- 생성자의 이름은 클래스 이름과 동일해야한다.
- 생성자는 리턴 값이 없다, 리턴 타입을 쓰지 않는다.
- 모든 클래스는 반드시 `한 개 이상의 생성자`를 가지고 있다.
- 사용자가 생성자를 정의하지 않으면, 컴파일러 시점에 자동으로 기본생성자를 만들어 준다.

### 생성자의 다중정의(constructor overloading)
동일한 클래스에서 동일한 이름의 생성자를 여러 개 정의하는 문법

### 형식
#### 기본 생성자(default constructor)

    [접근제한] 클래스이름() { }

```java
public Member() {  }
```

#### 매개변수가 있는 생성자

    [접근제한] 클래스이름(매개변수) {
    		생성자 호출 시 실행될 문장;
    }

```java
public Member(String n, int a, String p, String j) {
	name = n;
	age = a;
	phone = p;
	job = j;
}
```
- 매개변수를 인스턴스 초기화 작업에 사용

```java
// 기본생성자
Member mem1 = new Member();
mem1.name = "홍길동";
mem1.age = 25;
mem1.phone = "010-7546-4566";
mem1.job = "은행원";

// 매개변수가 있는 생성자
Member mem2 = new Member("이유리",28,"010-6531-5466","개발자");
```
- 인스턴스를 생성하고 값을 변경하는 것보다 매개변수를 갖는 생성자를 사용하는 것이 코드를 더 간결하고 직관적으로 만든다.

## 캡슐화
데이터를 외부에서 변경하지 못하도록 `외부의 접근을 제한`하는 것

- **private** : 외부에서 접근 차단
- **public** : 모든 클래스에서 접근 가능

### setter() / getter() 메서드로 접근 가능
#### setter() 
private 멤버변수에 값을 지정(`초기값 할당`)하는 역할을 하는 메서드

    public void set멤버변수명(자료형 매개변수) {
    		멤버변수 = 매개변수;
    }

```java
public void setNum1(int num1) {
	this.num1 = num1;
}
```
#### getter() 
private 멤버변수에 할당된 값을 `가져오는` 역할을 하는 메서드

    public 반환형 get멤버변수명() {
    	return 멤버변수명;
    }

```java
public int getNum1() {
		return num1;
}
```
### this
주로 멤버변수와 메서드 또는 생성자의 매개변수 이름이 동일할 때 인스턴스의 멤버임을 명확히 하기 위해 사용

- 멤버변수(전역변수) 앞에 this라는 키워드를 붙여 구분
- 지역변수와 전역변수의 이름이 같으면 우선순위는 지역변수가 높다.
```java
class Number {
	
	private int num1;
	private int num2;
	
	public void setNum1(int num1) {
		this.num1 = num1;
	}
	
	public void setNum2(int num2) {
		this.num2 = num2;
	}
	public int getNum1() {
		return num1;
	}
	
	public int getNum2() {
		return num2;
	}
}

public class Number_Main {

	public static void main(String[] args) {
		Number num = new Number();
		
		//num.num1 = 10000;	 외부에서 접근 X
		
		num.setNum1(10000);
		System.out.println("num1 : " + num.getNum1());
		
		num.setNum2(5000);
		System.out.println("num2 : " + num.getNum2());		
	}

}
```

## 객체배열
배열 안에 객체가 저장 되는 것이 아닌 `객체의 주소 값`이 저장된다.

<img src="https://user-images.githubusercontent.com/46274903/93580355-aa165b00-f9da-11ea-94ed-12f0f6510465.PNG " width="600"  height="">

### 구현

1. 객체 배열 생성
```java
Book[] books = Book[3];
```

2. 각 인덱스에 객체 생성
```java
books[0] = new Book();
books[1] = new Book();
books[2] = new Book();
```

## 상속(inheritance)
기존의 클래스를 `재사용`하여 새로운 클래스를 작성하는 것

<img src="https://user-images.githubusercontent.com/46274903/93748884-eb557780-fc33-11ea-8271-50af55efa134.PNG " width=""  height="">

- 자식과 부모의 관계로 형성
	- 부모클래스 :  Super, Parent 클래스
	- 자식클래스 :  Sub, Child 클래스

- 자식은 부모의 멤버보다 같거나 많다.
- 부모클래스를 변경하면 자식클래스는 자동으로 영향을 받지만 부모클래스는 자식클래스를 변경하여도 영향을 받지 않는다.
- 상속의 대상은 멤버(멤버변수, 멤버메서드)
	- 생성자, private 접근 제한을 갖는 멤버는 상속에서 제외된다.
- `단일 상속`만 가능

### 장점

> 코드의 재사용성을 높이고 코드의 중복을 제거하여 
> 프로그램의 생산성과 유지보수에 크게 기여

### 형식
	[접근제한] class 자식클래스 extends 부모클래스{ }
```java
class Circle extends Shape { }
```

### 포함(Composite)관계
클래스의 멤버변수로 다른 클래스 타입의 참조변수를 선언하는 것

```java
class Car{
	Engine e = new Engine();
	//...
}
```
- 포함관계 : ~은 ~을 가지고 있다.(has a)
- 상속관계 : ~은 ~이다.(is a)

### Object 클래스
java의 가장 `최상위 조상 클래스`

- 사용자가 정의한 클래스에 자동으로 상속

#### 관련 메서드

- **toString()** : 객체 자신의 정보를 문자열로 반환

- **getClass()** : 객체 자신의 클래스 정보를 담고 있는 Class 인스턴스를 반환
- **hashCode()** : 객체 자신의 해시코드를 반환
- **equals()** : 객체 자신과 또 다른 객체가 같은 객체인지 알려주는 메서드(boolean)
- **clone()** : 객체 자신의 복사본을 반환

### 오버라이딩(Overriding)
부모클래스에서 정의한 메서드를 자식 클래스에서 `재정의` 하는 것

- 반드시 `상속관계`에서만 발생
- 이름, 매개변수, 반환타입이 일치해야 한다.
- 접근지정자는 부모클래스의 메서드보다 좁은 범위로 변경할 수 없다.
	- default -> public (O) / default -> private (X)
- 부모클래스의 메서드보다 많은 수의 예외를 선언할 수 없다.

```java
class Point {
	int x;
	int y;

	void prn(){
		System.out.println("x : " + x + "y : " + y);
	}
}

class Point3D extends Point{
	int z;
	
	//overriding
	void prn(){
		System.out.println("x : " + x + "y : " + y + "z : " + z);
	}
}
```

### 오버로딩과 오버라이딩
**오버로딩** : 기존에 없는 메서드를 정의하는 것
**오버라이딩** : 상속받은 메서드의 내용을 재정의 하는 것

### super
자식클래스에서 부모클래스의 `멤버를 호출`하는 명령어

	 super.부모클래스멤버(멤버변수, 멤버메서드)

```java
class Car2{
	int cc;
	String color = "검정색";
}

class Avante extends Car2{
	String color = "흰색";
	
	void prn() {
		System.out.println("엔진 : " + cc +", 색상 : "+color);
		System.out.println("엔진 : " + cc +", 색상 : "+super.color);
		System.out.println("엔진 : " + cc +", 색상 : "+this.color);
	}
}
```
```
엔진 : 1600, 색상 : 흰색
엔진 : 1600, 색상 : 검정색
엔진 : 1600, 색상 : 흰색
```
### super()
자식클래스에서 부모클래스의 `생성자를 호출`하는 명령어

    super(인자);	// 인자생략가능

- 자식클래스 생성자의 `첫 줄`에서 부모클래스의 생성자를 호출해야한다.
	- 자식클래스의 멤버가 부모클래스의 멤버를 사용할 수 있도록 먼저 초기화가 되어있어야 하므로.
- super();을 호출하지 않았을 경우 컴파일러가 자동적으로 super();을 생성자 첫 줄에 삽입한다.

```java
class Point {
	int x;
	int y;
	
	public Point() { }	
	
	public Point(int x, int y) {
		this.x = x;
		this.y = y;
	}
}

class Point3D extends Point{
	
	int z;
	
	public Point3D() { super(); }
	
	public Point3D(int x, int y) {
		super(x,y);		// 부모 클래스에 Point(int x, int y) 생성자가 정의되어 있지 않으면 오류
	}
	
	void prn() {
		System.out.println("X 좌표 >>> "+ x);
		System.out.println("Y 좌표 >>> "+ y);
		System.out.println("Z 좌표 >>> "+ z);
	}
	
	public Point3D(int x, int y, int z) {
		this(x,y);		// public Point3D(int x, int y)
		this.z = z;
	}
}
```
## 추상클래스(abstract class)
`추상메서드`를 포함하는 클래스

- 추상메서드를 재정의하지 않으면 error 발생
- 추상클래스는 객체 생성이 불가능, 자식클래스를 대상으로 객체 생성
- 일반 멤버(멤버변수, 멤버메서드)를 가질 수 있다.

### 형식
	[접근제한] abstract class 클래스명 {		}

### 추상메서드
선언부만 작성하고 구현부(본체,body)는 작성하지 않은 메서드

- 추상클래스를 상속받는 자식클래스에서 재정의
- 추상클래스의 추상 메서드를 모두 구현해주어야 한다.
	- 하나라도 구현하지 않으면 자손클래스도 추상클래스로 지정

### 형식

    abstract 리턴타입 메서드이름();

```java
abstract class Super {	// 추상클래스
	int num1;
	
	int calc() {	/*	내 용 생 략	*/	}
	
	abstract void display();	// 추상메서드
}

class Sub extends Super{

	@Override
	void display() {	/*	내 용 생 략	*/	}

}
```
### 추상화와 구체화
**추상화** : 클래스간의 공통점을 찾아내서 공통의 조상을 만드는 작업
**구체화** : 상속을 통해 클래스를 구현, 확장하는 작업

## 인터페이스(interface)
일종의 추상클래스, 추상클래스보다 추상화 정도가 더 높다.
실제 구현된 것이 전혀 없는 기본 설계도

- `추상메서드와 상수만`을 멤버로 갖는다.
- 인스턴스를 생성할 수 없고, 클래스 작성에 도움을 줄 목적으로 사용된다. 
- 자식클래스로 객체를 생성, 인터페이스의 메서드 중 일부만 구현한다면 abstract를 붙여 추상클래스로 선언해야한다.
- 인터페이스도 상속을 받을 수 있다.
- `다중 상속 가능`, 상속 시 extends가 아닌 **implements**를 사용

### 형식
	interface 인터페이스이름 {
			public static final 타입 상수이름 = 값;
			public abstract 메서드이름(메개변수목록);
	}

- 모든 멤버변수는 상수(public static final) 로 인식
- 모든 메서드는 추상메서드(public abstract) 로 인식

```java
interface Inter{
	int num = 100;
	
	void display1();
	void display2();
}

class Sub implements Inter{

	@Override
	public void display1() {	/*	내 용 생 략	*/	}

	@Override
	public void display2() {	/*	내 용 생 략	*/	}
	
}
```
### 장점

> 개발시간 단축
> 
> 표준화 가능
> 
> 서로 관계없는 클래스들에게 관계를 맺어 줄 수 있다.
> 
> 독립적인 프로그래밍 가능

## 다형성(polymorphism)
`한 타입의 참조변수로 여러 타입의 객체를 참조`할 수 있는 것

- 조상클래스 타입의 참조변수로 자손클래스의 인스턴스를 참조할 수 있다.

- 반대로 자손타입의 참조변수로 조상타입의 인스턴스를 참조할 수는 없다.
- 다형성을 이용하여 부모의 참조변수로 자식의 객체를 생성했을 때 부모에는 없는 자식의 멤버를 호출할 수 없다.

```java
class Animal{
	
	void sound() {
		System.out.println("소리를 냅니다.");
	}
}

class Dog extends Animal{
	
	@Override
	void sound() {
		System.out.println("멍멍멍");
	}
	
	void prn(){	/* 내용 생략 */ }
	
}

class Cat extends Animal{
	@Override
	void sound() {
		System.out.println("야옹");
	}
}

public class Animal_Main {

	public static void main(String[] args) {
	
		// 다형성을 이용한 객체 생성 1
		Dog dog =new Dog();
		Animal animal = dog;
		
		// 다형성을 이용한 객체 생성 2
		Animal animal1 = new Dog();
		animal1.sound();
		
		// 다형성을 이용하여 부모의 참조변수로 자식의 객체를 생성했을 때
		// 부모에는 없는 자식의 멤버를 호출할 수 없다.
		animal1.prn();	// error
		
		Animal animal2 = new Cat();
		animal2.sound();
	}
}
```
### instanceof 연산자
참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아보기 위해 사용

- boolean(true/false)로 반환

```java
if(a instanceof Car)
```
- 참조변수 a의 타입이 Car 타입이라면 true, 아니라면 false
```java
if(a instanceof Vehicle)
```
- Vehicle이 Car 클래스의 조상클래스라면 true가 반환된다.

## final 지정자

#### 클래스 
- 변경할 수 없는 클래스, 확장될 수 없는 클래스
- final로 지정된 클래스는 다른 클래스의 조상이 될 수 없음
```java
public final class EE{		}

class AA extends EE{	}	// error
```
#### 멤버메서드 
- 변경될 수 없는 메서드
- final로 지정된 메서드는 오버라이딩을 통해 재정의 할 수 없음
```java
class AA {
	final void prn(){	/* 내용 생략 */ }
}

class BB extends AA{
	@Override
	void prn{	/* 내용 생략 */ }	// error
}
```
#### 멤버변수 
- 변경될 수 없는 변수 
- final로 지정된 변수는 값을 변경할 수 없다.
```java
class AA {
	final int aa = 100;
}

class BB extends AA{
	aa = 200;	// error
}
```
## 패키지(package)
서로 연관성이 있는 클래스들과 인터페이스들의 묶음

- 모든 클래스는 반드시 하나의 패키지에 속해야 한다.
- 패키지는 서브패키지를 가질 수 있으며, 점(.)으로 구분한다.

### import문
현재 패키지의 클래스에서 다른 패키지에 있는 다른 클래스를 사용하고 싶을 때 사용

#### 형식

    import 패키지명.클래스명;
    import 패키지명.*;

- 패키지명.* 은 지정된 패키지에 속하는 모든 클래스를 사용
- ctrl + shift  + o 를 누르면 자동으로 import 문 추가

## 접근 제어자(access modifier)
클래스, 멤버변수, 메서드, 생성자에서 사용

    private 	같은 클래스 내에서만 접근이 가능
    default 	같은 패키지 내에서만 접근이 가능
    protected 	같은 패키지 내에서, 그리고 다른 패키지의 자손클래스에서 접근이 가능
    public		모든 클래스에서 접근이 가능

## 익명 클래스(anonymous class)
이름이 없는 클래스

- interface 객체 생성 시 많이 사용
- 클래스의 선언과 객체의 생성을 동시에 하기 때문에 단 한번만 사용
- 하나의 객체만 생성할 수 있는 일회용 클래스
```java
Inter inter = new Inter() {
	
	@Override
	public int sum(int n1, int n2) {
		return n1 + n2;
	}
	
	@Override
	public int minus(int n1, int n2) {
		return n1 - n2;
	}
};
```

## 내부 클래스(inner class)
클래스 내에 선언된 클래스

- 두 클래스가 서로 긴밀한 관계일 경우 사용
- 내부 클래스를 하나의 멤버로 사용할 수 있음
- 내부 클래스는 외부 클래스의 멤버를 마치 자기 자신처럼 사용이 가능
- 외부 클래스 멤버의 접근지정자가 private 일지라도 접근 가능
- 내부 클래스의 접근은 반드시 외부 클래스를 통해 접근해야 함

```java
class Outer{		// 외부 클래스
	
	int su1 = 10;
	private int su2 = 34;
	
	class Inner{	// 내부 클래스
		
		void prn() {
			// 외부 클래스 멤버 접근 가능, private 또한 접근 가능
			System.out.println("su1 : " + su1);	
			System.out.println("su2 : " + su2);	
		}
		
	}
}
```
### 장점

> 내부 클래스에서 외부 클래스의 멤버들을 쉽게 접근할 수 있다.
> 
> 코드의 복잡성을 줄일 수 있다.(캡슐화)

### 형식
	외부클래스명.내부클래스명 참조변수 = 외부클래스참조변수.new 내부클래스 생성자();

```java
// 1. 외부 클래스 객체 생성
Outer outer = new Outer();

// 2. 내부 클래스 객체 생성
Outer.Inner inner = outer.new Inner();
```
