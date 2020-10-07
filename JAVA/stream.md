# 입출력(I/O)
컴퓨터 내부 또는 외부의 장치와 프로그램간의 데이터를 주고받는 것

## 스트림(Stream)
`데이터를 운반`하는데 사용되는 `연결통로`

- `단방향` 통신만 가능, 입출력을 동시에 처리할 수 없다.
- `FIFO(First In First Out)` 구조
- java.io 패키지에 있는 클래스를 이용하여 파일을 입출력

```java	
// System.in : 표준입력장치(키보드)
// read() : 표준입력장치를 통해서 입력받은 데이터를 읽음, 읽으면 ASCII 코드(숫자)로 반환
int num = System.in.read();
```


### 스트림 종류
1. **바이트 스트림** : `1바이트` 단위로 데이터를 입출력(byte)

**InputStream / OutputStream**

```java
InputStreamReader isr = new InputStreamReader(System.in);
```
<br/>

|  | 입력스트림 |출력스트림|
|--|--|--|
| 파일 | FIleInputStream | FileOutputStream |
| 메모리 |ByteArrayInputStream  | ByteArrayOutputStream |
| 프로세스|PipedInputStream  |PipedOutputStream |
| 오디오 | AudioInputStream|AudioOutputStream |
<br/>

> 파일

```java
InputStream is = null;
		
int readByte;
		
try {
	is = new FileInputStream("C:/test/sample.txt");
			
	while(true) {	
		readByte = is.read();
		
		// 더이상 읽을 데이터가 없다.
		if(readByte == -1) {
			break;
		}
		
		System.out.print((char)readByte);
	}
	is.close();
} catch (Exception e) {
	e.printStackTrace();
}
```
<br/>

2. **문자 스트림** : `2바이트` 단위로 데이터를 입출력(char)

**Reader / Writer**
<br/>


|  | 입력스트림 |출력스트림|
|--|--|--|
| 파일 | FIleReader  | FileWriter |
| 메모리 |ByteArrayReader   | ByteArrayWriter |
| 프로세스|PipedReader   |PipedWriter |
| 오디오 | AudioReader |AudioWriter |
<br/>

> 파일

```java
Reader isr = null;
		
int readByte;

try {
	isr = new FileReader("C:/test/sample.txt");
	
	while(true) {
		readByte = isr.read();
		
		if(readByte == -1) {
			break;
		}
		
		System.out.print((char)readByte);
	}
	
	isr.close();
} catch (Exception e) {
	e.printStackTrace();
}
```
<br/>

3. **보조 스트림** : 스트림의 `기능(속도)을 향상`시키거나 새로운 `기능을 추가`

- **BufferedInputStream(Reader)** / **BufferedOutputStream(Writer)** : 버퍼를 이용한 입출력 성능향상
- **InputStreamReader** / **OutputStreamWriter** : 바이트 스트림 -> 문자 스트림 변환
#### 형식
스트림을 먼저 생성한 후 보조스트림을 생성해야한다.

    BufferedReader 참조변수 = new BufferedReader(스트림참조변수);

```java
InputStreamReader isr = new InputStreamReader(System.in);
BufferedReader br = new BufferedReader(isr);
```
<br/>

## File 클래스
파일 및 디렉토리(폴더)를 생성하는 클래스

### 형식

    File 참조변수 = new File(경로);

```java
// 폴더 
File dir = new File("C:/sample");
// 파일
File file = new File(dir, "test");
```


### 관련 메서드

- *boolean* **mkdir()** : 새폴더 생성

- *boolean* **createNewFile()** : 새파일 생성
- *boolean* **exists()** : 해당 파일이 존재하면 true,  존재하지 않으면 false 반환
- *File[]* **listFiles()** : 디렉토리의 파일 목록을 File배열로 반환
- *long* **lastModified()** : 마지막 수정 시간 반환
- *String* **getName()** : 이름 반환
-  *String* **getParent()** : 파일의 조상 디렉토리 반환
- *String* **getPath()** : 파일 경로 반환

