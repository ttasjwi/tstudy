---

## <a href = "../../README.md" target="_blank">Collection Framework</a>

### 6. 정렬
#### 6.1 interface Comparable\<T>
1) interface Comparable\<T>
2) int compareTo()

---


# 6.1 interface Comparable\<T>

## 1) interface Comparable\<T>
```
public interface Comparable<T> {
    public int compareTo(T o);
}
```
- FQCN이 java.lang.Comparable임. 따라서 별도의 import문이 필요하지 아니함.
- 기본 정렬 기준을 지정하기위해 사용하는 인터페이스. 이 인터페이스를 구현해야 기본정렬기준에 따라 정렬하는 메서드들에 의해 정렬될 수 있다.
- 대부분의 java 라이브러리를 통해 제공되는 클래스들은 Comparable<T>의 구현체 
  - 예) 래퍼클래스(Integer, Double, ...) , String, LocalDate, LocalTime, ...

## 2) int compareTo(T o)
```
    public abstract int compareTo(T o);
```
- 실제 객체의 기본 정렬기준을 지정하기 위해 사용되는 인스턴스 메서드
- 인자 : 비교 대상이 되는 인스턴스
- 반환값(return value)의 부호에 따라 정렬 우선 순위가 결정된다.
  - 음수 : 앞에 정렬됨
  - 0 : 정렬 순위가 같다.
  - 양수 : 뒤에 정렬됨.

---