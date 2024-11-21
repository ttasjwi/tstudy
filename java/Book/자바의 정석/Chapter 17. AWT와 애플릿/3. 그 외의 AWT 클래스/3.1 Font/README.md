## <a href = "../../README.md" target="_blank">AWT와 애플릿(AWT & Applet)</a>

### 3. 그 외의 AWT 클래스
#### 3.1 Font
1) Font
2) Font의 생성자
3) 현재 시스템에 설치된 Font 가져오기

---

# 3.1 Font
## 1) Font
- Component에 사용되는 text의 글자체를 지정할 때 Font 클래스가 필요함. (반대로 적용된 폰트에 대한 정보를 얻어오는 메서드도 존재)
  - Font getFont() : 컴포턴트에 지정되어 있는 Font를 반환받음
  - void setFont(Font f) : 컴포넌트의 Font를 지정

---

## 2) Font의 생성자
- Font (String name, int style, int size)
  - name : 사용할 폰트의 이름
    - JDK에서 제공되는 기본 폰트 : Serif, SansSerif, Dialog, Dialog, DialogInput, Monospaced
    - 현재 사용 중인 시스템에 설치된 Font들을 얻어오기 위해서는 GraphicsEnvironment 클래스를 사용
  - style : 폰트의 스타일 지정 (보통 : FONT.PLAIN, 볼드 : Font.BOLD, 기울임 : Font.ITALIC, 굵은 기울임 : FONT.BOLD+FONT.ITALIC)
  - size : 폰트의 크기

---

## 3) 현재 시스템에 설치된 Font 가져오기

---