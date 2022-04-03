## <a href = "../../README.md" target="_blank">AWT와 애플릿(AWT & Applet)</a>

### 2. AWT의 주요 컴포넌트
#### 2.11 Panel
1) Panel
2) Panel의 메서드들

---

# 2.11 Panel
## 1) Panel
- 다른 컴포넌트를 자신의 영역 내에 포함시킬 수 있는 종속 컴포넌트.
  - 평면공간으로 Frame과 같이 여러 펌포넌트들을 담을 수 있지만, 단독적으로 사용할 수 없음.
- Panel 자신이 다른 컨테이너에 포함될 수도 있음. (Panel이 Panel에 포함되는 것도 가능)
- Frame과 달리 titlebar나 button이 없고, 비어있는 평면공간만을 가짐
- Frame 내에서 컴포넌트들의 배치를 다양하게 하는데 사용함. 
  - 컨테이너이기 대문에 자신만의 Layout을 유지할 수 있는 성질 활용

---

## 예제
```
import java.awt.*;

public class PanelTest {
    public static void main(String[] args) {
    
        // 프레임 생성 
        Frame frame = new Frame("Panel");
        frame.setSize(300, 200);
        frame.setLayout(null); // 프레임의 레이아웃 매니저를 지정하지 않음.
        
        // 패널 생성, 크기 및 위치 지정
        Panel panel = new Panel();
        panel.setBackground(new Color(138, 43, 226));
        panel.setSize(100,100);
        panel.setLocation(50, 50);

        //OK 버튼 생성
        Button button_OK = new Button("OK");

        //패널에 버튼을 추가하고, frame에 패널을 추가한다.
        panel.add(button_OK);
        frame.add(panel);
        frame.setVisible(true);
    }
}
```
![image](img/Panel_1.jpg)
- Frame에 레이아웃 매니저를 지정하지 않았으므로, Panel의 위치를 별도로 지정했음
- Button은 Panel에 포함되었으므로, Panel에 기본적으로 지정된 레이아웃 매니저의 영향을 받음.