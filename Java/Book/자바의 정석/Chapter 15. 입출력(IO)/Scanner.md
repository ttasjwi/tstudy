# Scanner 클래스

입력소스로부터 문자 데이터를 읽어오는 목적으로 사용되는 클래스
JDK 1.5부터 추가됨.

- 기존 입력 방식에서 불편했던 부분을 개선. 성능은 약간 떨어지는 부분이 있긴 하다.
- 정규식(Regular expression)을 이용한 라인단위 검색 지원
- 구분자(delimimeter)에 정규식 표현을 사용할 수 있어서 복잡한 형태의 구분자도 처리 가능

## 1.  생성

### 1)  import문
```
import java.util.Scanner;
```


### 2) 생성자
입력 소스에 따라 여러가지 생성자를 지원함

- Scanner(String source)
- Scanner(File source)
- Scanner(InputStream source)
    - 예) 화면 입출력 시 Scanner(System.in)을 생성하면 됨.
- Scanner (Readable source)
- Scanner (ReadableByteChannel source)
- Scanner (Path source) _// 1.7부터 추가_

## 2. 입력 및 반환
### 1) 입력

- 입력 소스로부터 값을 읽어와 버퍼에 저장
- 이 때 공백(' ','\s'), 탭문자('\t'), 개행자('\n') 등도 버퍼에 저장

### 2) 값의 반환 메서드
입력 소스로부터 받아온 값들을 여러 타입으로 반환받을 수 있음.
- 종류
    - boolean `nextBoolean()`
    - byte `nextByte()`
    - short `nextShort()`
    - int `nextInt()`
    - long `nextDouble()`
    - float `nextFloat()`
    - double `nextDouble()`
    - String `next()`
    - String `nextLine()` \*\*\*

- 주의점
    - 실제 입력한 데이터의 형식에 맞는 메서드를 사용하지 않으면 `InputMismatchException`이 throw 됨
    - `nextLine()` : 다음 개행자 '\n'까지 값을 가져와서(버퍼에서 해당 부분은 비워짐) 개행자 앞부분까지 반환함
    - `next()`, '`nextInt()` 등 다른 메서드들 : 다음 공백문자들까지 버퍼에서 값을 가져와서 반환하는데, 개행자('\n')는 가져오지 않음
    - 이런 점에서 next(), nextInt() 등에 이어서 nextLine() 등을 같이 쓸 때는 주의해야하는데, nextLine()을 한번 호출해서 버퍼를 비우도록 해야함.

### 3) 다음 값의 존재성
- boolean hasNextLine() : 다음 라인이 존재하는지 여부를 반환
- boolean hasNextInt() : 다음 숫자가 있는지 여부를 반환
- 그 외...

## 3. 구분자 사용

Scanner의 인스턴스 메서드들. 현재 Scanner 객체에 대해, 구분자를 지정하여 새로운 Scanner를 생성할 수 있다.

- Scanner useDelimiter(Pattern pattern) : Pattern 객체에 저장된 패턴(정규식)을 구분자로 한 Scanner 생성
- Scanner useDalimiter(String pattern) : 문자열로 된 패턴(정규식)을 구분자로 한 Scanner 생성

## 4. 알고리즘 풀 때
- 속도가 매우 느려서, BufferedReader를 쓰도록 하자.
- ~~알고리즘은 원래 java로 푸는거 아니래~~