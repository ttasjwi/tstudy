
---
## <a href = "https://github.com/ttasjwi/CodeSquad-Cocoa2021/tree/master/Note/Collection%20Framework" target="_blank">컬렉션 프레임워크</a>

### 1. 컬렉션 프레임워크(Collections FrameWork)

#### 1.1 컬렉션 프레임워크

1) 컬렉션 프레임워크란?  
2) 컬렉션 프레임워크의 주요 인터페이스

---

# 1.1 컬렉션 프레임워크란?

## 1) 컬렉션 프레임워크란?

컬렉션(다수의 객체)을 다루기 위한 표준화된 프로그래밍 방식. 컬렉션을 쉽고 편리하게 다루기 위함.

- Collection : 여러 객체(데이터)를 모아놓은 데이터 그룹.
- FrameWork : 표준화, 정형화된 체계적인 프로그래밍 방식

1. 컬렉션 프레임워크의 역사
    - JDK 1.2 이전 : 표준화되지 않은 컬렉션 클래스들(Vector, HashTable, Properties, ...) 등을 서로 다른 방식으로 처리
    - JDK 1.2 부터 : 여러 컬렉션 클래스들을 표준화된 방식으로 처리할 수 있음. 하지만 여전히 배열, Collection 인터페이스의 구현체, Map 인터페이스의 구현체,... 등의 처리 방식은 각각 다름.
    - JDK 1.8 이후 : Stream의 도입으로 데이터 처리 방식이 진정한 의미로 표준화됨

2. 컬렉션 프레임워크의 장점
    - 다수의 데이터를 다루는데 필요한 다양한 클래스들을 제공
    - 인터페이스, 다형성을 이용한 객체지향 설계를 통해 표준화됨
        - 여러 종류의 컬렉션들에 대해 매번 완전 다르게 사용법을 익힐 필요가 없어 익히기 간단함.
        - 재사용성이 높은 코드를 작성할 수 있음.

---

## 2) 컬렉션 프레임워크의 주요 인터페이스

1. Collection 인터페이스와 그 자손 인터페이스
    1) List : 순서가 있는 데이터의 집합. 데이터의 중복 허락
        - 예) ArrayList, LinkedList, Vector, Stack, ...
    2) Set : 순서가 유지하지 않는 데이터의 집합. 데이터의 중복을 허락하지 않음.
        - 예) HashSet, TreeSet, ...
2. Map 인터페이스와 그 자손
    1) Map
        - 키(key)와 값(Value)의 쌍(Map.Entry)으로 이루어진 데이터 집합
        - 순서유지 x, key의 중복 허락 x, value 중복 허락 o
        - 예) HashMap, HashTable, LinkedHashMap, ConcurrentHashMap, TreeMap, Properties, ...

---