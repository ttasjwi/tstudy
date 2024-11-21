
---

# 1. 컬렉션 프레임워크(Collections FrameWork)

## 1.1 <a href="https://github.com/ttasjwi/CodeSquad-Cocoa2021/blob/master/Note/Collection%20Framework/1.%20%EC%BB%AC%EB%A0%89%EC%85%98%20%ED%94%84%EB%A0%88%EC%9E%84%EC%9B%8C%ED%81%AC(Collections%20FrameWork)/CollectionFrameWork.md" target="_blank">컬렉션 프레임워크</a>
1. 컬렉션 프레임워크의 정의
2. 컬렉션 프레임워크의 주요 인터페이스

## 1.2 interface Collection\<E>
1. Collection<E>의 상속 및 구현
2. Collection<E>의 메서드

---

# 2. List

## 1) ArrayList
## 2) LinkedList
## 3) Stack, Queue, PrioriyQueue, Deque

---

# 3. Set

## 1) HashSet
## 2) TreeSet

---

# 4. Map

## 4.1 <a href="4. Map/4.1 interface Map/Map.md" target="_blank"> interface Map<K,V></a>
1. Map 인터페이스의 특징
2. Map 인터페이스의 주요 메서드
3. Map.Entry 인터페이스


## 4.2 HashMap, HashTable, ConcurrentHashMap
1. 자료구조 : 해시테이블
2. java에서의 해시테이블
3. HashMap
4. HashTable, ConcurrentHashMap
## 4.3 TreeMap
## 4.4 Properties

---

# 5. 접근
## Iterator, ListIterator, Enumeration

---

# 6. 정렬

정렬에 필요한 것
- 정렬 대상
- 정렬 대상을 모아둔 데이터군 : 배열, 컬렉션(List, Set, Map), Stream 
- 정렬 기준

## <a href="6. 정렬/6.1 interface Comparable/README.md" target="_blank">6.1 interface Comparable\<T></a>
1) interface Comparable\<T>
2) int compareTo()
## <a href="6. 정렬/6.2 interface Comparator/README.md" target="_blank">6.2 interface Comparator\<T></a>
1) interface Comparator\<T>
2) int compare(T o1, T o2);
3) 람다식으로 Comparator\<T> 표현하기
4) 여러가지 static 메서드
5) 여러가지 default 메서드
6) 유용한 Comparator 상수

## 6.3 정렬하기
- List의 sort()
  - default void sort(Comparator<? super E> c) : List인터페이스의 디폴트 메서드. 1.8부터 사용 가능.
- Arrays.sort()
  - public static void sort(Object[] a) : Comparable 구현에 의한 정렬
  - public static <T> void sort(T[] a, Comparator<? super T> c) : Comparator 구현에 의한 정렬
- Collections.sort()
  - public static <T extends Comparable<? super T>> void sort(List<T> list) : Comparable 구현에 의한 정렬
  - public static <T> void sort(List<T> list, Comparator<? super T> c) : Comparator 구현에 의한 정렬

- Stream의 sorted()


---

# 7. 유틸성 클래스

## Arrays
## Collections

---