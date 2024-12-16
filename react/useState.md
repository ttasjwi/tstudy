# useState - 상태 관리

---

#### 공식 문서
- [공식 Reference](https://react.dev/reference/react/useState)
- [비공식 한국어 번역](https://react-ko.dev/reference/react/useState): 2024년 12월 31일까지 유지

---

#### 개요
- 컴포넌트 단위로 관리 대상이 되는 상태를 선언하고, 상태를 변경할 수 있는 리액트 훅

---

#### useState
```jsx
import { useState } from 'react';

function MyComponent() {
  const [age, setAge] = useState(28);
  const [name, setName] = useState('Taylor');
  const [todos, setTodos] = useState(() => createTodos());
  // ...
```
- 관례적으로 구조 분해 할당을 사용하여 상태, 상태변경함수를 할당
  - `[something, setSomething]` : 첫번째 인자는 관리하고자 하는 상태, 두번째 인자는 상태 변경함수
- typescript 를 사용할 경우 상태의 타입을 지정할 것
  - 예) `useState<number>()`
- `useState(initialState)` 에서 initialState 에는 초기화 값 또는 초기화 값을 만드는 콜백함수를 전달한다.
  - 값 방식: 지정한 값이 초기값이 됨
  - 콜백함수 방식: 최초 1회만 호출됨

---

#### setXXX : 상태값 변경
- 상태값 변경을 위해서는 setXXX 를 호출해서 변경해야한다.
- 방식
  - `setXXX(값)`: 직접적으로 값을 지정하여 상태를 변경하는 방식
  - `setXXX(prev => 값)`: 콜백함수를 전달하여 상태를 변경하는 방식
- 상태 변경이 일어날 때 컴포넌트 함수를 다시 호출하여 화면을 다시 렌더링한다.
  - 다만 모든 요소를 다시 렌더링하는 것이 아니라, React 가상 Dom 트리 상에서 변경된 부분만 변경한다.
- 상태 변경은 일괄 처리된다.
  - 이벤트 핸들러가 모두 실행되고 나서야 컴포넌트 함수를 다시 호출하여 화면을 업데이트한다.
  - 이벤트 핸들러에서 setXXX 를 여러번 호출하였다면 그 함수를 모두 실행한다. 이 과정에서 업데이트 함수를 queue 에 넣고 순서대로 호출한다.
  - 업데이트 queue 의 모든 작업이 순서대로 처리되고 나서, 컴포넌트 함수 호출이 이루어진다.
  - setXXX 가 호출될 때마다 컴포넌트 호출을 하게 되면, 단일 이벤트를 처리할 때 컴포넌트 함수를 n번 호출할 수 있기 때문이다.

---

#### setXXX(...) 사용 시 주의점
```jsx
const [age, setAge] = useState(42);

function handleClick() {
    setAge(age + 1); // setAge(42 + 1)
    setAge(age + 1); // setAge(42 + 1)
    setAge(age + 1); // setAge(42 + 1)
}
```
- useState 를 호출하더라도 곧바로 age 의 상태가 변경되지 않는다. 위에서 언급했듯 이벤트 핸들러가 모두 실행되고
컴포넌트 함수를 호출할 때 반영된다.
- handleClick 함수를 호출한 시점에 age는 42 이고 그 시점의 age 상태는 변경되지 않는다.
  - handleClick 이 호출될 때 내부에서 사용하고 있는 외부 변수값을 스냅샷 찍어둠(렉시컬 환경)
  - handleClick 이 호출되면 렉시컬 환경의 42 를 가져와서 계속 setCount를 호출하게 되는데 count가 고정되어 있으므로 42 + 1 로 계속 수정됨

```jsx
const [age, setAge] = useState(42);

function handleClick() {
    setAge(prev => prev + 1); // setAge(42 => 43)
    setAge(prev => prev + 1); // setAge(43 => 44)
    setAge(prev => prev + 1); // setAge(44 => 45)
}
```
- setXXX(콜백) 콜백함수는 그 순간의 상태값을 인자로 사용한다.
- React는 콜백으로 전달한 업데이트 함수를 큐에 넣는다. 그런 다음, 렌더링 중에 삽입된 순서대로 콜백함수를 실행한다.
  - prev => prev + 1 : 42 -> 42 + 1
  - prev => prev + 1 : 43 -> 43 + 1
  - prev => prev + 1 : 44 -> 44 + 1
- 결론
  - useXXX(...) 에 상태값을 직접 전달하는 방법은 한 번 호출하는 경우에는 괜찮을 수 있다. 하지만 여러번 호출하는 경우 의도한 대로 동작하지
  않을 수 있다.
  - 콜백함수 방식을 사용하는 것이 가장 확실하다. 그 순간의 state 를 기반으로 작동하기 때문

---
