
---

## <a href = "https://github.com/ttasjwi/CodeSquad-Cocoa2021/tree/master/Note/Collection%20Framework" target="_blank">컬렉션 프레임워크</a>

### 1. 컬렉션 프레임워크(Collections FrameWork)

#### 1.2 interface Collection\<E>

1) Collection<E>의 상속 및 구현
2) Collection<E>의 메서드

---

# 1.2 interface Collection\<E>

List, Set 등 컬렉션의 조상 인터페이스.

## 1) Collection<E>의 상속 및 구현
- 조상 인터페이스 : Iterable<E>
- 자손 인터페이스 
  - List<E>, Set<E>, Queue<E>, Deque<E>, PriorityQueue<E>, NavigableSet<E>, SortedSet<E>, ...

- 주로 알려진 구현체들
  - ArrayList<E>, LinkedList<E>, Vector<E>, Stack<E>, HashSet<E>, TreeSet<E>,  ...

---

## 2) Collection<E>의 메서드  
1. 추가
   - boolean add(E e) : Collection에 지정 객체를 추가. 이 컬렉션이 호출의 결과로 변경되면 true를 반환.
   - boolean addAll(Collection<? extends E> c) : Collection에 지정 컬렉션의 모든 객체들을 추가.
2. 탐색 
   - boolean contains(Object o) : 지정 객체가 Collection에 포함되어있는지 여부를 반환
   - boolean containsAll(Collection<?> c) : 지정 Collection의 모든 요소가 Collection에 포함되어있는지 여부를 반환 
   - Iterator<E> iterator() : Collection의 iterator(전체 탐색)를 얻어서 반환
3. 제거
   - boolean remove(Obeject o) : 지정 객체를 삭제한다. 이 메서드 호출 결과, 요소가 삭제되면 true를 반환.
   - boolean removeAll(Collection<?> c) : 지정 Collection에 포함된 모든 요소를 찾아 제거한다. Collection이 변경되면 true를 반환 
   - boolean removeIf(Predicate<? super E> filter) : Collection에서 지정 조건을 만족하는 모든 요소를 제거
   - boolean retainAll(Collection<?> c) : 지정 Collection에 포함된 요소를 남기고 나머지 객체들은 제거한다. 이 작업으로 컬렉션에 변경이 있으면 true, 없으면 false를 반환
   - void clear() : 이 컬렉션의 모든 요소를 제거
4. 그 외
   - boolean isEmpty() : Collection이 비어있는지 반환한다.
   - boolean equals() : 동일한 Collection인지 비교
   - int size() : 지정 컬렉션에 포함된 객체의 개수를 반환한다.
   - Object[] toArray() : Collection에 저장된 객체를 객체배열 E[]로 반환
   - T[] toArray(T[] a) : 지정 배열에 Collection의 객체를 저장해서 반환
5. 스트림
   - Stream<E> stream() : 지정 컬렉션을 소스로 한 Stream 반환
   - Stream<E> parallelStream() : 지정 컬렉션을 소스로 하여, 병렬처리가 가능한 Stream을 반환
   - void ForEach(Consumer<? super E> action) : 지정 Collection의 모든 요소을 인자로 하여 각각 지정 action을 수행

---

참고문서 : <a href="https://docs.oracle.com/en/java/javase/11/docs/api/java.base/java/util/List.html" target="_blank">javaDocs</a>