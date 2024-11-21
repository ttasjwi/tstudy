
---

## <a href = "../../README.md" target="_blank">AWT와 애플릿 (AWT & Applet)</a>

### 1. AWT
#### 1.1 AWT

1. AWT(Abstract Window Toolkit)
2. GUI(Graphical User Interface)
3. CLI(Command-Line Interface)
4. AWT의 특징
5. Swing의 등장

---

# 1.1 AWT(Abstract Window Toolkit)

## 1) AWT란?
- Window 프로그래밍 (GUI 프로그래밍)을 위한 도구
- GUI 어플리케이션 개발에 필요한 관련된 패키지, 클래스의 집합으로 구성
- Windows와 같은 GUI, 어플리케이션 작성에 활용

## 2) GUI (Graphical User Interface)
- 사용자가 그래픽을 통하여 하드웨어와 상호작용하는 환경.
- 마우스 등을 이용하여, 화면의 메뉴 중에서 하나를 선택하여 작업을 지시할 수 있음.
- 창(Window), 스크롤바, 아이콘 이미지, 버튼(button) 등으로 구성됨
- Microsoft의 Windows, Apple의 Macintosh 등이 GUI의 대표적인 예

## 3) CLI (Command-Line Interface)
- 사용자가 가상 터미널 또는 터미널을 통하여 하드웨어와 상호작용하는 환경
- 컴퓨터 키보드 입력(명령어)으로 명령을 내리고, 결과가 문자로 표시됨
- CUI(Character User Interface)라고도 함.
- DOS, Command Prompt, UNIX 셸 등등이 CLI의 대표적인 예

## 4) AWT의 특징
- 플랫폼에 독립적이여서 여러 종류 OS에서 코드를 수정하지 않아도 실행 가능.
  - 플랫폼 : JVM가 설치될 수 있는 기반환경. 하드웨어 또는 OS가 이에 해당. MS Windows용 java의 플랫폼은 MS Windows(OS)이고, MS Windows의 플랫폼은 IBM 호환 컴퓨터(하드웨어)이다.
- 각 OS의 native Component 기반의 컴포넌트를 제공함
  - 컴포넌트 : 독립적인 기능을 가진 모듈. window, button 등의 구성요소가 이에 해당
  - 작성된 어플리케이션의 외양(appearance)이 실행 OS마다 달라질 수 있음.
  - 여러 종류의 GUI기반 OS들의 공통적인 native component만으로 구성해야하기 때문에, 제공 가능한 컴포넌트 수가 제한적
  - 해당 os에 최적화되어 있기 때문에 java로 구현한 컴포넌트보다 속도가 빠름.

## 5) Swing의 등장
- AWT의 확장. OS의 native 컴포넌트 기반이 아닌, 순수 java 기반
- AWT보다 다양한 기능의 컴포넌트 제공 -> GUI 애플리케이션 개발의 도구로 사용됨