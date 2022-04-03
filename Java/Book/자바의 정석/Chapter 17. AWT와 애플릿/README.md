
# AWT와 애플릿 (AWT & Applet)

java를 통해 GUI를 구현하기 위함

---

# 1. AWT

## <a href="1. AWT/1.1 AWT/README.md" target="_blank">1.1 AWT</a>

1) AWT(Abstract Window Toolkit)
2) GUI(Graphical User Interface)
3) CLI(Command-Line Interface)
4) AWT의 특징
5) Swing의 등장

## <a href="1. AWT/1.2 AWT의 구성/README.md" target="_blank">1.2 AWT의 구성</a>
1) AWT 관련 패키지들
2) 일반 컴포넌트
3) 메뉴 관련 컴포넌트

## <a href="1. AWT/1.3 컴포넌트(Component)/README.md" target="_blank">1.3 컴포넌트(Component)</a>
1) 모듈과 컴포넌트
2) GUI의 컴포넌트
3) public abstract class Component
4) Component의 주요 메서드

## <a href="1. AWT/1.4 컨테이너(Container)/README.md" target="_blank">1.4 컨테이너(Container)</a>
1) 컨테이너
2) 독립 컨테이너
3) 종속 컨테이너
4) 컨테이너에 다른 컴포넌트 포함시키기
5) Container의 메서드

---

# 2. AWT의 주요 컴포넌트
### <a href="2. AWT의 주요 컴포넌트/2.1 Frame/README.md" target="_blank">2.1 Frame</a>
### <a href="2. AWT의 주요 컴포넌트/2.2 Button/README.md" target="_blank">2.2 Button</a>
### <a href="2. AWT의 주요 컴포넌트/2.3 Choice/README.md" target="_blank">2.3 Choice</a>
### <a href="2. AWT의 주요 컴포넌트/2.4 List/README.md" target="_blank">2.4 List</a>
### <a href="2. AWT의 주요 컴포넌트/2.5 Lable/README.md" target="_blank">2.5 Lable</a>
### <a href="2. AWT의 주요 컴포넌트/2.6 Checkbox/README.md" target="_blank">2.6 Checkbox</a>
### <a href="2. AWT의 주요 컴포넌트/2.7 TextField/README.md" target="_blank">2.7 TextField</a>
### <a href="2. AWT의 주요 컴포넌트/2.8 TextArea/README.md" target="_blank">2.8 TextArea</a>
### <a href="2. AWT의 주요 컴포넌트/2.9 Scrollbar/README.md" target="_blank">2.9 Scrollbar</a>
### <a href="2. AWT의 주요 컴포넌트/2.10 Canvas/README.md" target="_blank">2.10 Canvas</a>
### <a href="2. AWT의 주요 컴포넌트/2.11 Panel/README.md" target="_blank">2.11 Panel</a>
### <a href="2. AWT의 주요 컴포넌트/2.12 ScrollPane/README.md" target="_blank">2.12 ScrollPane</a>
### <a href="2. AWT의 주요 컴포넌트/2.13 Dialog/README.md" target="_blank">2.13 Dialog</a>
### <a href="2. AWT의 주요 컴포넌트/2.14 FileDialog/README.md" target="_blank">2.14 FileDialog</a>

---

# 3. 그 외의 AWT 클래스
## <a href="3. 그 외의 AWT 클래스/3.1 Font/README.md" target="_blank">3.1 Font</a>
1) Font
2) Font의 생성자
3) 현재 시스템에 설치된 Font 가져오기
## <a href="3. 그 외의 AWT 클래스/3.2 Color/README.md" target="_blank">3.2 Color</a>
1) Color
2) Color의 생성자
---

# 4. 메뉴 만들기
## <a href="4. 메뉴 만들기/4.1 메뉴를 구성하는 컴포넌트/README.md" target="_blank">4.1 메뉴를 구성하는 컴포넌트</a>
1) MenuComponent와 그 하위클래스들
2) 메뉴 구성하기
3) 메뉴 관련 컴포넌트들의 메서드들
## 4.2 PopupMenu

---

# 5. 레이아웃 매니저
HTML의 `<div>`처럼, 컴포넌트를 화면 상에 배치하는 용도로 사용
## <a href="5. 레이아웃 매니저/5.1 레이아웃 매니저/README.md" target="_blank">5.1 레이아웃 매니저</a>
1) 레이아웃 매니저란?
2) AWT에서 제공되는 5가지 레이아웃 매니저
3) 컨테이너별 기본 레이아웃 매니저
## 5.2 BorderLayout
## 5.3 FlowLayout
## 5.4 GridLayout
## 5.5 CardLayout

---

# 6. 이벤트 처리(event handling)
## <a href="6. 이벤트 처리(event handling)/6.1 이벤트(event)/README.md" target="_blank">6.1 이벤트(event)</a>
1) 이벤트란?
2) 이벤트 소스(Event Source) : 이벤트 발생지
3) 이벤트 핸들러(Event Handler) : 이벤트 처리기
4) 이벤트 리스너(Event Listener) : 이벤트 감지기
5) 이벤트 처리(event handling)

## 6.2 이벤트의 발생과 처리
## 6.3 이벤트 처리방법
## 6.4 Adapter 클래스

---

# 7. AWT의 그래픽
## <a href="7. AWT의 그래픽/7.1 paint()와 Graphics/README.md" target="_blank">7.1 paint()와 Graphics</a>
1) paint()
2) Graphics
3) Graphics의 메서드들
## <a href="7. AWT의 그래픽/7.2 AWT 쓰레드와 repaint()/README.md" target="_blank">7.2 AWT 쓰레드와 repaint()</a>
1) AWT 쓰레드
2) AWT 쓰레드의 화면갱신 조건
3) repaint()
4) update(Graphics g)
5) 화면 갱신 과정
## 7.3 Image를 이용해서 이미지 출력하기

---

# 8. 애플릿(Applet)
## 8.1 애플릿(Applet)이란?
## 8.2 Applet의 생명주기(Life cycle)와 주요 메서드
## 8.3 Applet의 보안 제약(Security restriction)
## 8.4 Applet과 HTML 태그

---

# 연습문제

---