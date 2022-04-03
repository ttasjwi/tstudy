---

## <a href = "../../README.md" target="_blank">AWT와 애플릿 (AWT & Applet)</a>

### 1. AWT
#### 1.4 컨테이너(Container)
1) 컨테이너
2) 독립 컨테이너
3) 종속 컨테이너
4) 컨테이너에 다른 컴포넌트 포함시키기
5) Container의 메서드

---

# 1.4 컨테이너(Container)

## 1) 컨테이너
- Component의 하위 클래스인 Container 및 그 자손
- Component(Button, Label, ...)를 포함할 수 있다.
- 다른 Container를 포함할 수 있음.

---

## 2) 독립 컨테이너
독립적으로 사용될 수 있으며, 다른 컴포넌트나 종속 컨테이너를 포함할 수 있다.
- Frame
- Window
- Dialog

---

## 3) 종속 컨테이너
독립적으로 사용될 수 없으며, 다른 컨테이너에 포함되어야만 한다.
- Panel : 평면공간으로 Frame과 같이 여러 컴포넌트들을 담을 수 있으나 단독적으로 사용 불가.
- ScrollPane

---

## 4) 컨테이너에 다른 컴포넌트 포함시키기
- 컨테이너에는 여러개의 오버로딩된 add메서드가 정의됨. add 메서드를 사용하여, 다른 컴포넌트들을 포함시킬 수 있다.
- 컨테이너에 포함된 컴포넌트들은 기본적으로 컨테이너에 설정된 배경색(Background Color), 전경색(Foreground Color), 글자체(Font) 등의 설정을 그대로 따르게 됨

---

## 5) Container의  메서드
1. 추가
   - Component add(Component comp) : 컨테이너에 지정 컴포넌트를 추가
2. 제거
   - void remove(Component comp) : 컨테이너에서 지정 컴포넌트를 제거
3. 컴포넌트 반환
   - Component getComponent(int n) : 컨테이너에 n번째로 추가된 컴포넌트를 얻는다.
   - Component getComponentAt(int x, int y) : 컨테이너의 지정된 위치(x,y)에 있는 컴포넌트를 얻는다.
   - Component[] getComponents() : 컨테이너에 포함된 모든 컴포넌트를 얻는다.
4. 경계의 크기
   - Insets getInsets() : 컨테이너의 경계의 크기를 알 수 있는 Insets 객체를 반환
5. LayoutManager
   - LayoutManager getLayOut() : 컨테이너에 설정되어 있는 LayoutManager를 얻는다.
   - void setLayout(LayoutManager mgr) : 컨테이너에 LayoutManager를 설정한다.

---