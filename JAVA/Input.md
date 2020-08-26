# 키보드로 데이터를 입력받는 방법
1. main(String[] args)를 이용하는 방법

2. JOptionPane 클래스를 이용하는 방법

3. Scanner 클래스를 이용하는 방법

4. 파일 입출력을 이용하는 방법


### main(String[] args)를 이용하는 방법

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

