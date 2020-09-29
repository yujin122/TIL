# 컬렉션 프레임워크(Collections Framework)
데이터 추가, 수정, 삭제, 검색 등을 효과적으로 제공해 주는 자료구조 관련 클래스

- 컬렉션 클래스를 표준화하여 설계해놓은 인터페이스
- List 계열, Set 계열, Map 계열

## List

- 자료의 순서 보장(index)
- 중복 데이터 허용
- List 인터페이스의 자식클래스로 구현
	- ArrayList, LinkedList, Vector
- DB에 저장된 데이터를 레코드 단위로 저장하거나 가져올 경우 많이 사용

### ArrayList

**생성**

    ArrayList<T> 참조변수 = new ArrayList<T>();
    List<T> 참조변수 = new 자식클래스();

```java
ArrayList<String> list = new ArrayList<String>();

// 다형성으로 객체 생성
List<String> list = new ArrayList<String>();
```
<br/>

**관련 메서드**

- **add(element(*value*))** : 데이터 추가
```java
list.add("abc");
```
- **add(index, element(*value*))** : 특정 index에 데이트를 추가
```java
list.add(2,"b");
```
- **size()** : 데이터 크기 반환
```java
list.size()
```
- **get(*index*)** : 특정 요소(index) 출력
```java
list.get(3);
```
- **clear()** : 모든 요소 제거
```java
list.clear();
```
- **remove(*index*)** : 특정 요소(index)를 삭제
	- 다음 index부터 index 값이 한칸씩 당겨진다.
```java
list.remove(1);
```
<br/>

**단점**

> 용량을 변경해야할 때 상당히 효율이 떨어짐
<br/>

### LinkedList

- 인접 참조를 링크해서 체인처럼 관리
- 특정 인덱스에서 객체를 제거하거나 추가하게 되면 앞 뒤의 링크만 연결하면 된다.
- 빈번한 객체의 삽입과 삭제가 일어나는 곳에서는 ArrayList보다 더 큰 성능을 발휘

**생성**
```java
LinkedList<Integer> list=new LinkedList<Integer>();

// 다형성으로 객체 생성
List<Integer> list = new LinkedList<Integer>();
```
<br/>

### Stack

- LIFO(Last In First Out) 구조

**생성**

```java
Stack<String> stack = new Stack<String>();
```
<br/>

**관련 메서드**

- **push()** : 스택에 저장
```java
stack.push("abc");
```
- **peek()** : stack의 맨 위에 있는 데이터를 가져옴, 가져온 데이터를 제거하지 않음.
```java
stack.peek()
```
- **pop()** : stack의 맨 위에 있는 데이터를 가져옴, 가져온 데이터를 stack에서 제거.
```java
stack.pop()
```
<br/>

### Queue

-  FIFO(First In First Out) 구조
- 인터페이스이므로 자식클래스로 객체 생성해서 사용
- 대표적인 자식클래스는  LinkedList


**생성**

```java
Queue<String> queue = new LinkedList<String>();
```
<br/>

**관련 메서드**

- **offer()** : 큐에 저장
```java
queue.offer("abc");
```
- **peek()** : queue의 맨 위에 있는 데이터를 가져옴, 가져온 데이터를 제거하지 않음.
```java
queue.peek()
```
- **poll()** : queue의 맨 위에 있는 데이터를 가져옴, 가져온 데이터를 queue에서 제거.
```java
queue.poll()
```
<br/>

## Set 

- 자료의 순서가 없다.
- 중복 데이터를 허용하지 않는다.
-  Set 인터페이스의 자식클래스를 이용하여 구현
	-  HashSet, TreeSet


**생성**
```java
Set<Integer> set = new HashSet<Integer>();
```
<br/>

## Map

- 키(key)와 값(value)을 하나의 쌍으로 묶어서 저장
- 키 중복 X, 값 중복 O
- Map 인터페이스의 자식클래스를 이용하여 구현
	- Hashtable, HashMap, TreeMap

**생성**
```java
Map<String, Integer> map = new HashMap<String, Integer>();
```
<br/>

**관련 메서드**

- **put(*key, value*)** : 데이터 저장
```java
map.put("abc", 95);
```
- **get(*key*)** : key에 해당하는 value 값을 반환
```java
map.get("abc");
```
- **containsKeys(*value*)** : 값과 동일한 key가 존재하면 true / 존재하지 않으면 false
```java
map.containsKey("abc");
```
<br/>

## Iterator
컬렉션에 `저장된 요소를 접근`하는데 사용되는 인터페이스

**생성**

    Iterator<T> 참조변수 = 컬렉션참조변수.iterator();

```java
Iterator<String> it = list.iterator();
```
<br/>

**관련 메서드**

- **hasNext()** : 읽어올 요소가 남아있는지 확인 (true/false)
```java
it.hasNext();
```
- **next()** : 다음 요소를 읽어옴
```java
it.next();
``` 

