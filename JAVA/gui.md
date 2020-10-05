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

#### 2. BorderLayout
`동, 서, 남, 북, 중앙`에 배치

**형식**

    컨테이너(프레임)참조변수.setLayout(new BorderLayout(컴포넌트 정렬 방법(수평간격, 수직간격))

```java
jp.setLayout(new BorderLayout(40, 30));

jp.add(jb1, BorderLayout.NORTH);
jp.add(jb2, BorderLayout.SOUTH);

```
		
#### 3. GridLayout
격자 모양의 배치관리자, `행과 열`로 화면이 구성된다.

**형식**

    컨테이너(프레임)참조변수.setLayout(new GridLayout(행, 열, 수평간격, 수직간격))

```java
jp.setLayout(new GridLayout(4,3,5,5));
```


