---

## <a href = "../../README.md" target="_blank">컬렉션 프레임워크</a>
    
### 4. Map

#### 4.1 interface Map<K, V>

1) Collection<E>의 상속 및 구현
2) Collection<E>의 메서드

---

# 4.1 interface Map<K,V>

키(Key), 값(Value)을 하나의 쌍(Entry)로 묶어서 저장하는 컬렉션 클래스를 구현하는데 사용

## 1) Map 인터페이스의 특징
1. 순서 없음.
2. 중복 허용 여부
   - Key : 중복 허용 x
   - Value : 중복 허용 o
   - 기존에 저장된 데이터와 같은 Key를 가진 새로운 데이터를 put하면 기존 값이 없어지고, 새로운 값이 남음.
3. Type Parameter
   - K : 이 Map에서 관리하는 Key의 type
   - V : 이 Map에서 key에 연결된 Value의 type
4. 자손 인터페이스
   - Bindings, ConcurrentMap<K,​V>, ConcurrentNavigableMap<K,​V>, NavigableMap<K,​V>,SortedMap<K,​V>

5. 주요 구현 클래스
   - HashMap, HashTable, ConcurrentHashMap, CurrenteLinkedHashMap, TreeMap, Properties, ...

---

## 2) 주요 메서드
1. 추가
   - V put(K key, V value) : key-value 쌍을 연결(mapping)하여 저장. key가 중복되면, 새로 덮어씌운다.
   - void putAll(Map <? extends K, ? extends V> m) : 지정 Map의 모든 Key-value 쌍을 추가한다.
2. 반환
   - V get(Object key) : 지정 key 객체에 대응하는 value 객체를 찾아서 반환한다.
   - Set<Map.Entry<K,V>> entrySet() : Map에 저장되어 있는 key-value쌍을 Map.Entry타입의 객체로 저장한 Set을 반환한다.
   - Set<K> keySet() : Map에 저장되어 있는 key들을 저장한 Set을 반환한다.
   - Collection<V> values() : Map에 저장되어 있는 모든 value객체를 Collection으로 반환한다.
3. 검색
   - boolean containsKey(Object key) : 지정 key에 대응하는 value가 있으면 true를 반환한다.
   - boolean containsValue(Object value) : 지정 value에 대응하는 key가 1개 이상 존재하면 true를 반환한다.
4. 삭제
   - V remove(Object key) : 지정 key 객체와 일치하는 key-Value쌍을 삭제한다.
   - void clear() : Map의 모든 객체를 삭제한다.
5. Lambda, Stream 관련
6. 기타
   - int size() : Map에 저장된 key-value 쌍의 개수를 반환한다.
   - boolean equals() : 동일한 Map인지 비교
   - boolean isEmpty() : Map이 비어있는지 여부를 반환
   - int hashCode() : 해시코드 반환

---

## 3) Map.Entry 인터페이스
Map<K,V> 인터페이스의 내부 인터페이스.

- 주요 메서드(기본 라이브러리 구현체들 기준)
  - K getKey() : Entry의 Key 객체를 반환한다.
  - V getValue() : Entry의 Value 객체를 반환한다.
  - int hashCode() : Entry의 hashCode를 반환한다.
  - V setValue() : Entry의 Value객체를 지정 객체로 바꾸는 역할을 수행함.


---