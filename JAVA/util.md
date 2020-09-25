# Util 패키지 주요 클래스
### 1. Random 클래스
지정된 범위 내에서 임의의 난수를 발생시키는 클래스

**형식)**

	nextInt(가장 큰 수) + 시작 수

```java
Random random = new Random();
	int num = 0;
	
	for(int i=1;i<=6;i++) {
		num = random.nextInt(45)+1;
		System.out.print(num + "\t");
}
```
```
18	10	29	13	22	28	
```
### 2. Math 클래스
수학과 관련된 메서드를 제공해 주는 클래스

#### 관련 메서드

- **max()** / **min()** : 최대값, 최소값 을 구하는 메서드
```java
int num1 = 57, num2 = 41;

System.out.println("최대값 >>> " + Math.max(num1, num2));
System.out.println("최소값 >>> " + Math.min(num1, num2));
```
```
최대값 >>> 57
최소값 >>> 41
```
- **round()** : 반올림이 적용되는 메서드
```java
System.out.println(123.5124);
System.out.println(Math.round(123.5124));
```
```
123.5124
124
```
- **abs()** : 절대값을 구하는 메서드
```java
System.out.println("abs >>> " + Math.abs(-54.2));
```
```
abs >>> 54.2
```
- **ceil()** : 무조건 올림을 해주는 메서드
```java
System.out.println("ceil >>> " + Math.ceil(57.365));
```
```
ceil >>> 58.0
```
### 3. Calendar 클래스
날짜, 시간 관련된 정보를 제공해 주는 클래스

- 추상클래스
- 날짜와 시간을 계산하는데 꼭 필요한 메서드나 상수로 구성되어 있다.
- getInstance() 메서드를 이용하여 시스템의 날짜와 시간 정보를 표현
- **getInstance()** : 싱글턴 방식, 하나의 인스턴스만을 가지고 공유해서 사용할 때 쓰는 방법

#### 관련 메서드

- 날짜 정보를 확인하는 방법
```java
Calendar cal = Calendar.getInstance();

int year = cal.get(Calendar.YEAR);			// 현재 년도
System.out.println("현재 연도 : " + year + "년");
	
int month = cal.get(Calendar.MONTH) + 1;	// 현재 월
System.out.println("현재 월 : " + month + "월");

int day = cal.get(Calendar.DAY_OF_MONTH);	// 현재 일
System.out.println("현재 일 : " + day + "일");

int week = cal.get(Calendar.WEEK_OF_YEAR);	// 1년 52주 중 몇번 째 주인지 확인
System.out.println("현재 주 : " + week + "주");
```
```
현재 연도 : 2020년
현재 월 : 9월
현재 일 : 25일
현재 주 : 39주
```
- 시간 정보를 확인하는 방법
1. 12시간제를 사용하는 방법 - 오전(0), 오후(1)
```java
int am_pm = cal.get(Calendar.AM_PM);	// 오전 or 오후인지 확인하는 방법
int hour = cal.get(Calendar.HOUR);		// 몇 시
int minute = cal.get(Calendar.MINUTE);	// 몇 분
int second = cal.get(Calendar.SECOND);	// 몇 초			

if(am_pm == 0) {
	// 오전인 경우
	System.out.println("현재 시간 : 오전(AM) " + hour + "시 " + minute + "분 " + second + "초" );
}else {
	// 오후인 경우
	System.out.println("현재 시간 : 오후(PM) " + hour + "시 " + minute + "분 " + second + "초" );
}
```
```
현재 시간 : 오후(PM) 0시 41분 48초
```
2. 24시간제를 사용하는 방법
```java
int hours = cal.get(Calendar.HOUR_OF_DAY);

System.out.println("현재 시간 : " + hours + "시 " + minute + "분 " + second + "초" );
```
``` 
현재 시간 : 12시 41분 48초
```
### 3. Arrays 클래스
배열 객체를 처리하는 클래스

#### 관련 메서드

- **fill()** : 배열의 요소를 특정한 값(데이터)으로 채우는 메서드
```java
Arrays.fill(str, "abc");
for(String k:str) {
	System.out.println("str 배열 요소 : " + k);
}
```
```
str 배열 요소 : abc
str 배열 요소 : abc
str 배열 요소 : abc
```
- **equals(객체, 객체)** : 두 객체의 내용(데이터)이 같은지 틀린지 비교하는 메서드
```java
String[] str2 = {"abc", "abc", "abc"};

if(Arrays.equals(str, str2)) {
	System.out.println("두 객체의 내용(데이터)은 같습니다.");
}else {
	System.out.println("두 객체의 내용(데이터)은 다릅니다.");
}
```
```
두 객체의 내용(데이터)은 같습니다.
```
- **sort()** : 배열의 원소(데이터)를 정렬(오름차순)하는 메서드
```java
int[] arr = {54, 67, 13, 97, 41};
		
for(int k:arr) {
	System.out.print(k + "\t");
}
System.out.println();

Arrays.sort(arr);
for(int k : arr) {
	System.out.print(k + "\t");
}
```
```
54	67	13	97	41	
13	41	54	67	97	
```
