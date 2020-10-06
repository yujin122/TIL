# GUI(Graphic User Interface)
이미지 혹은 그래픽을 이용하여 메뉴 등을 포함하는 화면을 구성하고, 키보드 외 마우스 등의 입력 도구들을 이용하여 사용자가 입력하기 편하도록 만들어진 `사용자 인터페이스`

- 자바 언어는 GUI 프로그램을 쉽게 작성할 수 있도록 다양한 GUI 컴포넌트 제공
	- AWT 컴포넌트, Swing 컴포넌트

## AWT

- java.awt 패키지를 통해 공급
- 운영체제의 도움을 받아 화면에 출력되기 때문에 운영체제의 자원을 많이 소모하여 운영체제에 많은 부담을 줌
- 운영체제마다 컴포넌트의 모양이 다르게 나옴

## Swing

- javax.swing 패키지를 통해 공급
- 운영체제의 도움을 받지 않는다. -> 경량 컴포넌트라고 불림
- 운영체제와 관계 없이 항상 동일한 모양이 나타남
- AWT에 없는 풍부한 고급 Swing 컴포넌트들을 추가적으로 개발

## GUI 용어
1. **컴포넌트** : 버튼, 텍스트상자, 레이블상자, 옵션박스, 체크박스, 라디오박스 등 

2. **컨테이너** : 컴포넌트를 담을 수 있는 클래스
	-	컴포넌트는 반드시 컨테이너에 올려져야 화면에 보여짐
3. **프레임** :  컨테이너를 담을 수 있는 클래스
	-	컨테이너는 반드시 프레임에 올려져야 화면에 보여짐

## Frame
#### 1. Frame 클래스를 상속 받아 생성자를 통해 화면에 Frame을 보여주는 방법
 ```java
 import java.awt.Frame;		// awt 패키지
 
 public class Ex01 extneds Frame{
	public Ex01(){
			setTitle("Ex01");
			setLocation(100, 100);
			setSize(300, 300); 
			setVisible(true);
	}	
	public static void main(String[] args) {		
			new Ex01();
	}
}
```

#### 2. Frame 클래스의 객체를 생성해서 사용

**awt 패키지**
```java
Frame frame=new Frame("두번째 예제");		// 생성자에 직접 제목 설정
//frame.setTitle("두번째 예제");
		
// 프레임의 위치 + 크기
frame.setBounds(100, 100, 300, 300);
		
frame.setVisible(true);
}
```
**swing 패키지**
```java
JFrame jf = new JFrame("swing");

jf.setBounds(100, 100, 300, 300);
jf.setVisible(true);
```
<br/>

**관련 메서드**

- **setTitle("제목")** : frame 제목 설정
```java
jf.setTitle("예제");
```
- **setLocation(*x, y*)** : frame 위치 설정
- **setSize(*width, height*)** : frame 크기 설정
- **setBounds(*x, y, width, height*)** : frame 위치, 크기 동시 설정
```java
jf.setBounds(100,100,400,600);
```
- **setVisible()** : frame을 화면에 보여주는 메서드 (기본값 : false)
```java
jf.setVisible(true);
```
- **setResizeable()** : frame의 크기를 고정
```java
jf.setResizable(false);
```
- **setDefaultCloseOperation()** : frame X버튼을 클릭 시 종료시키는 메서드
```java
jf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
```
<br/>

## 컨테이너 
**형식**

    JPanel 참조변수 = new JPanel();

```java
JPanel jp = new JPanel();
```


##### * 컨테이너는 프레임에 올려야 화면에 보여진다.
```java
jf.add(jp);
```
<br/>

## 컴포넌트
####  1. Button
<img src="https://user-images.githubusercontent.com/46274903/94664384-c654b900-0345-11eb-8828-f983b373b517.PNG " width=""  height="">

**형식**

    JButton 참조변수 = new JButton("버튼내용")

```java
JButton button = new JButton("버튼1");
```
##### * 컴포넌트는 컨테이너에 올려야 화면에 보여진다.
```java
jp.add(button);
```
<br/>

**관련 메서드**

- 버튼 비활성화
```java
button.setEnabled(false);
```
- 이미지 아이콘 적용
```java
JButton button = new JButton(cheey);
```
<br/>

#### 2. 이미지 아이콘
**형식**

    ImageIcon 참조변수 = new ImageIcon("이미지 경로")

```java
ImageIcon cheey = new ImageIcon("images/cherry.jpg");
```
<br/>

#### 3. CheckBox
<img src="https://user-images.githubusercontent.com/46274903/94664449-db314c80-0345-11eb-94c4-3adf6c508e13.PNG " width=""  height="">

**형식**

    JCheckBox 참조변수 = new JCheckBox("내용")

```java
JCheckBox jcb1 = new JCheckBox("게임");
```
- 이미지 아이콘 적용
```java
JCheckBoxMenuItem jcb1 = new JCheckBoxMenuItem("사과", apple);
```
<br/>

#### 4. RadioButton
<img src="https://user-images.githubusercontent.com/46274903/94664530-f3a16700-0345-11eb-935d-e5e60e9323c3.PNG " width=""  height="">

**형식**

    JRadioButton 참조변수 = new JRadioButton("내용")

```java
JRadioButton jrb1 = new JRadioButton("게임");
```
* 라디오 버튼은 반드시 **ButtonGroup**에 올려야한다.<br/>
-> 안올리면 다중선택 가능
```java
ButtonGroup bg = new ButtonGroup();
		
bg.add(jrb1); bg.add(jrb2);
```
<br/>

#### 5. ToggleButton
<img src="https://user-images.githubusercontent.com/46274903/94664610-0a47be00-0346-11eb-9a2b-1ea6817c045a.PNG " width=""  height="">

**형식**

    JToggleButton 참조변수 = new JToggleButton("내용")

```java
JToggleButton jtb1 = new JToggleButton("토글버튼1");
```
<br/>

#### 6. ComboBox
<img src="https://user-images.githubusercontent.com/46274903/94664641-17fd4380-0346-11eb-80b7-be626dd5ccf0.PNG " width=""  height="">

**형식**

    JComboBox<T> 참조변수 = new JComboBox<T>(콤보박스에 들어갈 배열)

```java
JComboBox<String> jcb = new JComboBox<String>(job);
```
<br/>


#### 7. List
<img src="https://user-images.githubusercontent.com/46274903/94664676-24819c00-0346-11eb-80d0-f7f71631d3a0.PNG " width=""  height="">

**형식**

    JList<T> 참조변수 = new JList<T>(리스트에 들어갈 배열)

```java
JList<String> jl = new JList<String>(job);
```
<br/>

#### 8. Lable & TextField
<img src="https://user-images.githubusercontent.com/46274903/94664713-3105f480-0346-11eb-88fa-e0ea7356400d.PNG " width=""  height="">

**형식**

    JLabel 참조변수 = new JLabel("내용");
    JTextField 참조변수 = new JTextField(크기);

```java
JLabel jl1 = new JLabel("이 름 : ");
JTextField name = new JTextField(15);
```
<br/>

#### 스크롤 기능
**형식**

    JScrollPane 참조변수 = new JScrollPane(스크롤바가 보여질 컴포넌트,  수직 스크롤,  수평 스크롤)

```java
JScrollPane jsp = new JScrollPane(
				jt, 	
				ScrollPaneConstants.VERTICAL_SCROLLBAR_AS_NEEDED,	
				ScrollPaneConstants.HORIZONTAL_SCROLLBAR_NEVER		
				);
```
<br/>

#### 9. TabbedPane
<img src="https://user-images.githubusercontent.com/46274903/95046155-8bc09700-071e-11eb-88ee-babf5cc68bd1.PNG" width=""  height="">


 **형식**
 

     JTabbedPane 참조변수 = new JTabbedPane();

```java
JTabbedPane tab = new JTabbedPane();

// 각각의 컨테이너를 탭에 올려준다.
tab.add("버튼 탭", jp1);
tab.add("체크박스 탭", jp2);
tab.add("라디오버튼 탭", jp3);

// 4. 탭을 프레임에 올려준다.
jf.add(tab);
```
<br/>

#### 10. Menu

<img src="https://user-images.githubusercontent.com/46274903/95046524-4bade400-071f-11eb-9451-e68faeef3c04.PNG" width=""  height="">

**형식**

    JMenuBar 참조변수 = new JMenuBar();
    JMenu 참조변수 = new JMenu("메뉴이름");
    JMenuItem 참조변수 = new JMenuItem("아이템이름");

```java
JMenuBar bar = new JMenuBar();

// 메뉴 만들기
JMenu jMenu1 = new JMenu("파일");

// 메뉴 아이템 만들기
JMenuItem jmi1 = new JMenuItem("새파일");

// 메뉴에 메뉴아이템 추가
jMenu1.add(jmi1);

// 메뉴 사이에 경계선
jMenu1.addSeparator();

// 메뉴바에 메뉴 추가
bar.add(jMenu1);
```
<br/>

## 배치관리자(Layout)
화면에 컴포넌트들을 `배치`하는 방법을 알려주는 관리자

#### 1. FlowLayout
상단 중앙에 컴포넌트를 배치하고 `좌에서 우`로 컴포넌트를 추가한다.

- 화면이 넘칠 경우 바로 아래 중앙에 배치
- 배치관리자 default 값

**형식**

    컨테이너(프레임)참조변수.setLayout(new FlowLayout(컴퓨넌트 정렬방법(왼쪽, 오른쪽, 중앙), 수평간격, 수직간격))

```java
jp.setLayout(new FlowLayout(FlowLayout.LEFT, 30, 40));
```
<br/>

#### 2. BorderLayout
`동, 서, 남, 북, 중앙`에 배치

**형식**

    컨테이너(프레임)참조변수.setLayout(new BorderLayout(컴포넌트 정렬 방법(수평간격, 수직간격))

```java
jp.setLayout(new BorderLayout(40, 30));

jp.add(jb1, BorderLayout.NORTH);
jp.add(jb2, BorderLayout.SOUTH);

```
<br/>

#### 3. GridLayout
격자 모양의 배치관리자, `행과 열`로 화면이 구성된다.

**형식**

    컨테이너(프레임)참조변수.setLayout(new GridLayout(행, 열, 수평간격, 수직간격))

```java
jp.setLayout(new GridLayout(4,3,5,5));
```
<br/>

## Event Handler(이벤트 핸들러)
각 컴포넌트에 대하여 특정 행위를 하였을 때 그 행위에 대한 작업을 처리할 수 있도록 하는 것

### 이벤트 관련 용어

- **이벤트 소스** : 이벤트를 발생시킨 GUI 컴포넌트
- **이벤트 객체** : 발생한 이벤트에 대한 정보를 담는 객체
- **이벤트 리스너**(Event Listener) : 이벤트를 처리하는 코드로서 컴포넌트에 등록이 되어야 작동이 가능
- **이벤트 분배 스레드** : 이벤트 기반 프로그래밍의 핵심 요소로서 무한루프를 실행하는 스레드
<br/>

### 이벤트 동작 과정

> ex) 버튼 클릭 시

1. 사용자가 마우스로 버튼을 클릭
2. 버튼 클릭은 운영체제의 마우스 드라이버를 거쳐 자바 가상기계(JVM)에 전달
3. 자바가상기계는 이벤트 분배 스레드에게 마우스 클릭에 관한 정보를 전달
4. 이벤트 분배 스레드는 `이벤트(ActionEvent) 객체`를 생성, 
5. 이벤트 분배 스레드는 JButton에 연결된 버튼 컴포넌트와 관련된 `이벤트 리스너를 찾아서 호출`
6. 이벤트 분배 스레드는 다음 이벤트를 기다림
<br/>

### 이벤트 리스너 작성 과정

1. **이벤트와 이벤트 리스너 선택**
2. **이벤트 리스너 클래스 작성** : 리스너 인터페이스를 상속받은 클래스를 작성하고 추상메서드를 모두 구현
3. **이벤트 리스너 등록** : 이벤트를 받을 컴포넌트에 이벤트 리스너 등록
<br/>

### 이벤트 처리 방법

1. **ActionListener**를 상속 받기

```java
public class Ex24_Event extends JFrame implements ActionListener{
	
	JLabel result;
	
	public Ex24_Event() {
		
		super("이벤트 테스트");
		
		JPanel panel = new JPanel();
		
		JButton male = new JButton("남자");
		JButton female = new JButton("여자");
		
		JLabel label = new JLabel("당신의 성별은? ");
		result = new JLabel();
		result.setForeground(new Color(219,68,85));

		panel.add(male); panel.add(female); panel.add(label); panel.add(result);

		add(panel);
		
		// 이벤트를 받을 컴포넌트에 이벤트 리스너 등록
		male.addActionListener(this);
		female.addActionListener(this);
		
		setBounds(200, 100, 300, 100);
		setDefaultCloseOperation(EXIT_ON_CLOSE);
		setVisible(true);
		
		
	}
	
	// 이벤트가 발생했을 때 처리할 내용을 작성할 메서드
	@Override
	public void actionPerformed(ActionEvent e) {
		// 이벤트를 처리한 컴포넌트(버튼)의 타이틀(문자열)을 가져오는 메서드 
		result.setText(e.getActionCommand());	
	}
	
	public static void main(String[] args) {
		new Ex24_Event();
	}
}
```
<br/>

2. **무명클래스**로 이벤트 처리

```java
public class Ex25_Event extends JFrame{
	JLabel result;
	
	public Ex25_Event() {
		
		super("이벤트 테스트");

		JPanel panel = new JPanel();
		
		JButton male = new JButton("남자");
		JButton female = new JButton("여자");
		
		JLabel label = new JLabel("당신의 성별은? ");
		result = new JLabel();
		result.setForeground(new Color(219,68,85));
		
		panel.add(male); panel.add(female); panel.add(label); panel.add(result);
		
		add(panel);
		
		setBounds(200, 100, 300, 100);
		setDefaultCloseOperation(EXIT_ON_CLOSE);
		setVisible(true);
		
		// 이벤트 처리 - 무명클래스로 이벤트 처리
		// male 버튼을 클릭했을 때 이벤트 처리
		male.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
				result.setText(e.getActionCommand());
			}
		});
		
		// female 버튼을 클릭했을 때 이벤트 처리
		female.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
				result.setText(e.getActionCommand());
			}
		});
		
		
	}
		
	public static void main(String[] args) {
		new Ex25_Event();
	}
}
```
<br/>

3. **독립된 클래스** 작성

```java
public class Ex26_Event {

	public static void main(String[] args) {
		
		JFrame jf = new JFrame("버튼 이벤트 처리");
		
		JPanel jp = new JPanel();
		
		JButton button = new JButton("JAVA");
		
		// 이벤트 관련 독립된 클래스를 생성
		MyButton listener = new MyButton();
		
		button.addActionListener(listener);
		
		jp.add(button);
		
		jf.add(jp);
		
		jf.setBounds(200, 200, 300, 300);
		jf.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		jf.setVisible(true);
		
		
	}
}

// 독립된 클래스를 작성하여 이벤트 처리.
class MyButton implements ActionListener{
	
	public MyButton() {	}

	@Override
	public void actionPerformed(ActionEvent e) {
		
		JButton button = (JButton)e.getSource();
		
		if(button.getText().equals("JAVA")) {
			button.setText("자바");
		}else {
			button.setText("JAVA");
		}
	}
	
}
```
