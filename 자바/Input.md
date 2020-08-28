# 키보드로 데이터를 입력받는 방법
1. main(String[] args)를 이용하는 방법

2. JOptionPane 클래스를 이용하는 방법

3. Scanner 클래스를 이용하는 방법

4. 파일 입출력을 이용하는 방법


### main(String[] args)를 이용하는 방법
1. 선언

	    String  s = args[0]
- args 값은 String이므로 다른 자료형으로 사용하려면 따로 형변환을 해줘야한다.
2. 값 입력
	1. 네모박스 안에 있는 ▼를 누른다
![enter image description here](img/java_1.jpg)
	2.  Run Configurations -> Java Application -> Arguments 로 들어간다.
![enter image description here](img/java_2.jpg)
	3. Program arguments 박스에 값을 입력한다. 값이 여러개인 경우 enter로 구분.
![enter image description here](img/java_3.jpg)
3. Run

### JOptionPane 클래스를 이용하는 방법

### Scanner 클래스를 이용하는 방법
1. Scanner 클래스의 객체 생성

		Scanner scanner = new Scanner(System.in);

2. 입력한 내용 반환

	    String input = scanner.nextLine(); // 입력받은 내용을 input에 저장
	    int num = Integer.parseInt(input); // 입력받은 문자열을 int타입의 정수로 변환

- next(), nextLine()은 문자열로 저장하기때문에 다른 타입으로 반환하기 위해서는 `해당 타입으로 변환`시켜주어야한다. 
- 또는 nextInt(), nextFloat()와 같이 변환없이 숫자로 바로 입력받는 메서드들을 사용한다.

### 파일 입출력을 이용하는 방법

