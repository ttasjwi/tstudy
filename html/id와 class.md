# id 와 class

---

#### id
```html
<p id="special">난 특별해!</p>
<p>그... 그렇군요</p>
```
```javascript
const content = window.special.textContent;
```
```css
#special {
    font-size: 50px;
} 
```
- id 는 그 문서 전체에서 고유해야하는 식별자를 정의한다.
- 어떤 요소 단 하나에만 정의해야한다. 
- 목적
  - 링크 연결: [Uri - 프래그먼트 식별자](https://developer.mozilla.org/en-US/docs/Web/URI#fragment)
  - 스크립팅( javascript ) 또는 스타일링( CSS 사용 ) 시 단일 요소를 식별하기 위함
- reference: [mdn-id](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/id)

---

#### class
```html
<p>난 그냥 그래</p>
<p class="nice pretty">난 멋지고 예뻐</p>
<p class="nice">난 멋져</p>
```
```css
.nice {
  font-style: italic;
  font-weight: bold;
}
.pretty {
  background: rgb(255, 0, 0, 0.25);
  padding: 10px;
}
```
```javascript
const niceElements = document.getElementsByName("nice");
```
- class 는 여러 요소의 공통적인 속성의 명칭에 해당하는 개념을 의미한다.
- 여러 요소에 동시에 적용 가능하다.
- 한 요소에, 공백 문자열(' ')을 통해 여러개 지정할 수 있다.
- 목적
  - CSS 에서 클래스 선택자(`.xxx`) 를 통해 요소를 선택하고 스타일을 적용할 수 있다.
  - JavaScript 에서 `document.getElementsByClassName()` 함수를 통해 요소를 선택하고 액세스 할 수 있다.
- reference: [mdn - class](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/class)

---
