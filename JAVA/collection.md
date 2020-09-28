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
    List<T> 참조변수 = new ArrayList<T>();

```java
ArrayList<String> list = new ArrayList<String>();

// 다형성으로 객체 생성
List<String> list = new ArrayList<String>();
```

**관련 메서드**

- **add(element(값))** : 데이터 추가
```java
list.add("abc");
```
- **add(index, element(값))** : 특정 index에 데이트를 추가
```java
list.add(2,"b");
```
- **size()** : 데이터 크기 반환
```java
list.size()
```
- **get(index)** : 특정 요소(index) 출력
```java
list.get(3);
```
- **clear()** : 모든 요소 제거
```java
list.clear();
```
- **remove(index)** : 특정 요소(index)를 삭제
	- 다음 index부터 index 값이 한칸씩 당겨진다.
```java
list.remove(1);
```

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
