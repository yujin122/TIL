# 프로세스(process)

**실행 중인 프로그램**

- OS로부터 실행에 필요한 메모리를 할당 받음

# 스레드(Thread)
프로세스의 자원을 이용해 실제로 작업을 수행하는 것, `실제 프로그램이 수행되는 작업의 최소 단위`

- 프로세스에 `최소한 하나` 이상의 스레드가 존재
- 둘 이상의 스레드를 가진 프로세스 -> 멀티스레드 프로세스
- 하나의 프로세스가 가질 수 있는 스레드의 개수는 제한이 없음

### 멀티스레딩
여러 개의 `스레드`가 동시에 작업 
-> 아주 짧은 시간 동안 `여러 작업을 번갈아 가며 수행`함으로써 여러 작업이 동시에 수행되는 것 처럼 보임

**멀티태스킹** : 여러 개의 `프로세스`가 동시에 실행
<br/>

#### 장점

> CPU의 사용률 향상
> 
> 자원을 효율적으로 사용
> 
> 사용자에 대한 응답성 향상
> 
> 작업의 분리로 코드 간결
> 
<br/>

### 구현
#### 1. Thread 클래스 상속(extends)
```java
class Thread1 extends Thread {
	public void run() {		/* 작업내용 */	}	// run() 메서드 오버라이딩
}

public static void main(String[] args){
	Thread1 t = new Thread1();
	
	// start() : 스레드 클래스의 run() 메서드 실행
	t.start();
}
```
#### 2. Runnable 인터페이스 구현(implements)
`재사용성`이 높고 코드의 `일관성`을 유지할 수 있다.

```java
class Thread1 implements Runnable {
	@Override
	public void run() {		/* 작업내용 */	}	// run() 메서드 구현
}

public static void main(String[] args){
	// Runnable 인스턴스 생성
	Runnable r = new Thread1();
	// Thread 클래스 생성자 인자에 Runnable 참조변수 기재
	Thread t = new Thread(r);
	
	r.start();
}
```
<br/>

### 멀티스레드
하나의 스레드 클래스를 대상으로 2개 이상의 스레드 객체를 생성하는 기법

- 멀티스레드는 자신의 이름을 가지고 있음
- 스레드의 이름은 큰 역할을 하지는 않지만, 디버깅 시 어떠한 스레드가 현재 실행되어 작업하는지를 조사(확인)할 목적으로 사용

```java
class Thread1 extends Thread {
	public ThreadA() {	}
	
	public ThreadA(String name) {
		// 멀티스레드에서 생성한 스레드 객체에 이름을 부여
		super(name);
	}
	
	public void run() {		/* 작업내용 */	}	// run() 메서드 오버라이딩
}

public static void main(String[] args) {
	
	// ThreadA 클래스를 대상으로 멀티스레드 객체 생성
	ThreadA t1 = new ThreadA("첫번째 스레드");
	ThreadA t2 = new ThreadA("두번째 스레드");
	ThreadA t3 = new ThreadA("세번째 스레드");
	ThreadA t4 = new ThreadA("네번째 스레드");
	ThreadA t5 = new ThreadA("다섯번째 스레드");
	ThreadA t6 = new ThreadA("여섯번째 스레드");
	
	t1.start(); t2.start(); t3.start();
	t4.start(); t5.start(); t6.start();
}
```
<br/>

### 관련 메서드

- *Thread* **currentThread()** : 현재 실행중인 스레드의 참조 반환
- *String* **getName()** : 스레드의 이름 반환
<br/>

### 스레드의 실행제어

- **sleep**(*millis*) : 현재 실행중인 스레드를 `잠시 정지`시키는 메서드
```java
Thread.sleep(2000);
```
- **interrupt**() : 스레드의 `작업을 취소`하는 메서드
```java
tt.interrupt();
```
<br/>

### 스레드 동기화
스레드가 진행 중인 작업을 다른 스레드가 간섭하지 못하도록 막는 것

- **임계영역**(critical section) : 공유 데이터를 사용하는 코드 영역
-  **잠금**(lock) : lock을 획득한 하나의 스레드만 임계영역 내의 코드를 수행, 끝내면 lock 반납

### synchronized
`임계 영역을 설정`하는데 사용

#### 1. 메서드 전체를 임계 영역으로 지정
```java
public synchronized void sum() {
	// ....
}
```

#### 2. 특정한 영역을 임계 영역으로 지정
코드 일부를 블럭{}으로 감싸고 블럭 앞에 synchronized를 붙여 임계 영역으로 지정
```java
synchronized(객체의 참조변수){
		// ...
}
```
