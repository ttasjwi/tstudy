---

## <a href = "../../README.md" target="_blank">AWT와 애플릿 (AWT & Applet)</a>

### 1. AWT
#### 1.3 컴포넌트(Component)

1. 모듈과 컴포넌트
2. GUI의 컴포넌트
3. public abstract class Component
4. Component의 주요 메서드

---

# 1.3 컴포넌트(Component)

Component : 일반 컴포넌트의 최상위 추상 클래스
MenuComponent : Menu 관련 컴포넌트의 최상위 추상 클래스

## 1) 모듈과 컴포넌트
- 모듈 : 구조의 단위, 기능의 단위. 파트 및 컴포넌트의 집합
- part : 구조의 최소단위
- component : 기능의 최소단위

## 2) GUI의 컴포넌트
- 화면에 표시되어, 사용자와 상호작용 할 수 있는 그래픽 표현 기능의 최소단위
- GUI의 button, checkbox, scrollbar 등이 이에 해당

## 3) public abstract class Component
public abstract class Component  
extends Object
implements ImageObserver, MenuContainer, Serializable

- AWT 컴포넌트의 최상위 추상 클래스

## 4) Component의 주요 메서드
1. 배경색 
   - Color getBackGround() : 컴포넌트의 배경색 Color을 반환받음
   - void setBackGround(Color c) : 컴포넌트의 배경색을 지정
2. 커서 (마우스 포인터)
   - Cursor getCursor() : 컴포넌트에 지정된 커서 Cursor를 반환받음
   - void setCursor(Cursor c) : 컴포턴트의 커서를 지정한다.
3. 폰트
   - Font getFont() : 컴포턴트에 지정되어 있는 Font를 반환받음
   - void setFont(Font f) : 컴포넌트의 Font를 지정
4. 전경색(?)
   - Color getForeGround() : 컴포턴트의 전경색 Color을 반환받음
   - void setForeGround(Color c) : 컴포넌트의 전경색을 지정
5. 컴포넌트의 위치, 크기
   - Point getLocation() : 컴포넌트의 위치(x,y)를 얻는다.
   - void setLocation(int x, int y) : 컴포넌트의 위치를 지정한다.
   - int getWidth() : 컴포넌트의 폭(Width)를 반환받음
   - int getHeight() : 컴포넌트의 높이(Height)를 반환받음
   - Dimension getSize() : 컴포넌트의 크기 Dimension을 반환받는다.
   - void setSize(int width, int height) : 컴포넌트의 크기(width, height)를 지정한다.
   - Rectangle getBounds() : 컴포넌트의 위치와 크기 객체 Rectangle를 얻는다.
   - void setBounds(int x, int y, int width, int height) : 컴포턴트의 위치(x,y) 및 크기(width, height)를 지정
6. focus
   - boolean hasFocus() : 컴포넌트가 현재 focus를 갖고 있는지 알려줌
   - void requestFocus() : 컴포넌트가 foucus를 갖도록 한다.
7. 화면에 그리기
   - void paint(Graphics g) : 컴포넌트를 화면에 그린다.
   - void repaint() : 컴포넌트를 화면에 다시 그린다.
8. 컨테이너(Container)
   - Container getParent() : 컴포넌트가 포함되어 있는 컨테이너(parent)를 얻는다.
9. 그 외
   - void setEnabled(boolean b) : 컴포넌트를 사용가능(true) 또는 사용 불가능(false)하게 한다.
   - void setVisible(boolean b) : 컴포넌트를 화면에 보이게(ture) 또는 보이지 않게(false) 한다.