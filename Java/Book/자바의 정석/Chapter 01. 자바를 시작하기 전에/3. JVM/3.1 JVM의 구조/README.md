## <a href = "../../README.md" target="_blank">Basics in Java</a>

### 3. JVM
#### 3.1 JVM의 구조
1) Class Loader
2) JVM Memory Areas
3) Execution Engine
4) Native Method Interface
5) Native Method Libraries

---
# 3.1 JVM의 구조
![image](img/JVM_Architecture.png)

---

## 1) Class Loader
`.class` 파일의 바이트 코드를 읽고, 메모리에 적재하는 역할
1. loading : 클래스를 읽어오는 과정
2. linking : 레퍼런스를 연결하는 과정
3. initialization : static 값들을 초기화 및 변수에 할당하는 과정

---

## 2) JVM Memory Areas
실제 실행 프로그램 정보가 적재되는 메모리 공간

1. 공유 자원
   - Method Area
     - 클래스로더를 통해 읽어들인 클래스 수준의 정보(클래스 풀네임, 상위 클래스 풀네임, 메서드, 변수, ...)
   - Heap Area
     - 인스턴스 저장. 공유자원
2. 각 쓰레드의 영역(각 쓰레드마다)
   - Stack Area : 메서드 호출 정보를 Stack Frame이라는 블럭으로 쌓음. 모든 stackFrame이 사라진 쓰레드는 종료된다.
   - PC(Program Counter) Registers : 현재 실행중인 명령(Stack Frame)의 위치를 가리키는 포인터
   - Native Method Stack : native 메서드들의 호출정보가 쌓이는 스택
---

## 3) Execution Engine
Memory 영역에 할당된 바이트 코드를 실제 실행하는 영역.

1. 인터프리터(Interpreter) : 바이트 코드를 한 줄씩 기계어로 번역하고 실행.
2. JIT Compiler : 인터프리터의 효율을 높이기 위해, 인터프리터가 반복되는 코드를 발견하면 JIT 컴파일러에서 반복되는 코드를 모두 기계어로 바꿔둠. 이후 인터프리터는 번역된 반복 코드를 바로 바로 실행한다.
3. GC(Garbage Colector) : 더 이상 참조되지 않는 객체를 모아서 정리

---

## 4) Native Method Interface(JNI)
- Native Method Area와 상호작용하여, 실행에 필요한 Native Method Libraries를 제공
- Native로 작성된 코드들을 호출하는 인터페이스 역할
    - 예> java.lang.Thread.currentThread()
    ```
        public static native Thread currentThread();
    ```
---
    
## 5) Native Method Libraries
- 실제 C, C++로 작성된 라이브러리, 작성 코드
- 직접 참조되지 못 하고, JNI를 통해 참조될 수 있다.
---

유용한 링크들
https://javapapers.com/core-java/java-jvm-run-time-data-areas/#Program_Counter_PC_Register
https://dzone.com/articles/jvm-architecture-explained
https://blog.jamesdbloom.com/JVMInternals.html
https://www.geeksforgeeks.org/jvm-works-jvm-architecture/
