
---

## 1. 자료구조 : 해시테이블
(key, Value) 로 데이터들을 저장하는 자료구조.

1. hash함수
   - key에 대하여 hash함수를 거쳐 hash값을 반환받음. 이 hash값은 해시테이블 내부배열의 고유 index에 대응됨
     - 동일한 key에 대하여, 동일한 hash 값이 대응되어야함.
     - 동일한 key에 대하여 여러 hash값이 대응되면 value를 저장, 검색하기 힘들어짐.
   - 여기서 얻어진 index를 활용하여 value를 저장하거나, 검색할 수 있음.
2. 충돌
   - 서로 다른 key값에 대하여 동일 hash값이 나올 수 있음.
   - 이렇게 충돌되는 문제를 해결하기 위해 보통 분리 연결법 또는 개방주소법을 사용함.
     - 분리연결법 : 충돌데이터들을 LinkedList 등의 자료구조를 활용해 추가 메모리를 할당 후, 저장
     - 개방주소법 : 충돌이 발생할 경우 비어있는 해시테이블의 공간을 활용하여 다른 index에 할당함.

---

## 2. java의 해시테이블 자료구조
1. hash 함수 : 각 객체의 hashCode() 값을 기준으로 해싱함. hashCode는 int이므로 -2^31 ~ 2^31-1의 값에 대응됨.
   - 충돌 문제 : 분리연결법을 사용함. LinkedList 형태의 자료구조를 활용하여 저장.
   - 동일 hashCode값일 경우 equals()를 이용하여 서로 같은지 다른지 여부를 판단한다.
     - equals()가 true이면 같은 key로 인식한다.
     - equals()가 false이면 다른 key로 인식하여 LinkedList상의 다른 위치에 저장된다.
2. 해시테이블 자료구조가 사용된 컬렉션
   - HashSet, HashTable, HashMap, ConcurrentHashMap, ...

---

## 3. hashCode(), equals()의 오버라이딩
1. 필요성
   - 어떤 key가 어떤 기준으로 서로 같냐 다르냐를 확실하게 정의하기 위해 hashCode(), equals()를 함께 오버라이딩 해야함.
   - 오버라이딩 되어 있지 않은 경우 대다수의 경우 객체의 주솟값을 기준으로 반환하게 됨
2. 방법
   - 어떤 멤버변수를 기준으로 서로 같은 객체인지 아닌지를 결정한다.
   - boolean equals(Object o)
     - 객체의 타입이 다르면 false를 반환하도록 함 (instanceof 활용)
     - 객체의 타입이 같으면 위에서 결정한 멤버변수가 서로 같은지 여부를 기준으로 true/false를 반환하도록 해야함.
   - int hashCode()
     - 위에서 결정한 기준 멤버변수를 토대로 hashCode를 반환하도록 하면 됨
     - JDK 1.8 이전에는 여러 방식으로 hashCode를 생성했었는데 1.8 이후 기준으로는 Objects.hash(Object ... values)를 활용하면 됨
3. 잘못 오버라이딩 했을 경우 생기는 문제들
   - 별도의 오버라이딩이 제대로 되지 않았을 경우 : 같은 멤버변수가 저장된 key더라도 다른 index에 할당되어 애초부터 서로 다른 위치에 저장됨
   - hash값의 충돌이 빈번한 경우 : key가 서로 다르다면, 같은 LinkedList를 통해 연결된 자료량이 많아져서 자료 접근속도가 매우 나빠질 수 있음
   - hash값이 같고 equals()가 false일 경우 : 같은 index를 반환받지만 서로 다른 객체로 간주되어 LinkedList의 다른 위치에 저장됨

---

## 4. HashMap<K, V>
- Map 인터페이스의 구현체
- key-value를 연결(mapping)해서 하나의 데이터(Map.Entry)로 저장


