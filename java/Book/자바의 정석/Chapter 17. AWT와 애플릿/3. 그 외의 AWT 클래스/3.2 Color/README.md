## <a href = "../../README.md" target="_blank">AWT와 애플릿(AWT & Applet)</a>

### 3. 그 외의 AWT 클래스
#### 3.2 Color
1) Color
2) Color의 생성자

---

# 3.2 Color
## 1) Color
- 색을 표현하기 위해 사용하는 클래스
- 원하는 색의 RGB 값을 알고 있으면, 그 색을 표현할 수 있는 객체를 생성하여 사용할 수 있다.
- 자주 쓰이는 13가지 색상들은 static 멤버 변수로 정의되어 있음.
- 사용처 : 컴포넌트의 배경색, 전경색 설정
  - Color getBackGround() : 컴포넌트의 배경색 Color을 반환받음
  - Color getForeGround() : 컴포턴트의 전경색 Color을 반환받음
  - void setBackGround(Color c) : 컴포넌트의 배경색을 지정
  - void setForeGround(Color c) : 컴포넌트의 전경색을 지정
---

## 2) Color의 생성자
- Color(int r, int g, int b) : r - red, g- green, b - blue (0~255 사이의 정숫값)
  - Color (int r, int g, int b, int a) : a - 0~255 사이의 정숫값. 값이 클 수록 불투명하다.
- Color (float r, float, g, float b) : r - red, g-green, b - blue (0.0~1.0 사이의 실숫값)
  - Color (float r, float g, float b, float a) : a - 0.0~1.0 사이의 실숫값. 값이 클 수록 불투명해진다.

---
