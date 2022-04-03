

# Lambda & Stream

---

# 1. 람다식(Lambda Expression)

## <a href="1. 람다식(Lambda Expression)/1.1 람다식(Lambda Expression).md" target="_blank">1.1 람다식(Lambda Expression)</a>
1) 람다식이란?
2) 함수 vs 메서드
3) 일급 객체
4) 익명 클래스
5) 메서드를 일급 객체처럼
6) 순수함수
7) 고차함수

## <a href="1. 람다식(Lambda Expression)/1.2 람다식 작성하기.md" target="_blank">1.2 람다식 작성하기</a>
1) 람다식 작성

## <a href="1. 람다식(Lambda Expression)/1.3 함수형 인터페이스(Functional Interface).md" target="_blank">1.3 함수형 인터페이스(Functional Interface)</a>
1) 함수형 인터페이스
2) 함수형 인터페이스 타입의 매개변수
3) 함수형 인터페이스 타입의 반환타입
4) 메서드의 일급객체 취급
5) 람다식의 타입과 형변환
6) 익명 객체의 타입
7) 외부 변수를 참조하는 람다식

--- 

# 2. java.util.function 패키지

## <a href="2. java.util.function 패키지/2.1 여러가지 함수형 인터페이스.md" target="_blank">2.1 여러가지 함수형 인터페이스</a>
1) 핵심 함수형 인터페이스
2) 매개변수가 두 개인 함수형 인터페이스
3) 매개변수가 3개 이상인 경우는?
4) UnaryOperator, BinaryOperator
5) 기본형을 사용하는 함수형 인터페이스

## <a href="2. java.util.function 패키지/2.2 컬렉션 프레임워크와 함수형 인터페이스.md" target="_blank">2.2 컬렉션 프레임워크와 함수형 인터페이스</a>
1) `Iterable<T>` 인터페이스의 디폴트 메서드
2) `Collection<T>` 인터페이스의 디폴트 메서드
3) `List<E>` 인터페이스의 디폴트 메서드
4) `Map<K,V>` 인터페이스의 디폴트 메서드

## <a href="2. java.util.function 패키지/2.3 Function의 합성과 Predicate의 결합.md" target="_blank">2.3 Function의 합성과 Predicate의 결합</a>
1) Function의 합성
2) 항등함수
3) Predicate의 결합
4) 동등 여부를 판단하는 Predicate

## <a href="2. java.util.function 패키지/2.4 메서드 참조.md" target="_blank">2.4 메서드 참조</a>
1) 메서드 참조란?
2) static 메서드 참조
3) 임의의 객체마다 특정 인스턴스 메서드 참조
4) 특정 객체의 인스턴스 메서드 참조
5) 생성자의 메서드 참조

---

# 3. Stream

## <a href="3. Stream/3.1 Stream.md" target="_blank">3.1 Stream</a>
1) Stream이란?
2) 기존 데이터군 처리방식의 한계
3) Stream의 편리성
4) Stream을 통한 작업의 흐름
5) Stream의 특징

## <a href="3. Stream/3.2 Stream 생성.md" target="_blank">3.2 Stream 생성</a>
1) 컬렉션 기반 Stream
2) 가변인자, 배열 기반 Stream
3) 특정 범위의 정수
4) 난수 Stream
5) 람다식 기반 Stream - iterate(), generate()
6) 파일 기반
7) 빈 스트림
8) 두 스트림의 연결

## <a href="3. Stream/3.3 기본형 Stream.md" target="_blank">3.3 기본형 Stream</a>
1) 기본형 Stream 생성
2) 기본형 Stream의 최종연산
3) summaryStatistics

---

# 4. Stream의 중간연산

## <a href="4. Stream의 중간연산/4.1 자르기, 걸러내기.md" target="_blank">4.1 자르기, 걸러내기</a>
1) skip - 앞의 n개 건너뛰기
2) limit - 요소를 n개로 제한
3) filter - 지정 조건에 부합하는 요소만 남김(필터링)
4) distinct - 중복 제거

## <a href="4. Stream의 중간연산/4.2 정렬.md" target="_blank">4.2 정렬</a>
1) 정렬의 필요조건
2) Stream의 정렬 - sorted()  
3) <a href="../Collection Framework/6. 정렬/6.2 interface Comparator/README.md" target="_blank">Comparator\<T> 재학습</a>

## <a href="4. Stream의 중간연산/4.3 변환.md" target="_blank">4.3 변환</a>
1) 변환 - map
2) flatMap
3) mapToInt, ...
4) flatMapToInt, ...

## <a href="4. Stream의 중간연산/4.4 중간확인.md" target="_blank">4.4 중간확인</a>
1) peek

---

# 5. Optional과 OptionalInt

## <a href="5. Optional과 OptionalInt/5.1 Optional.md" target="_blank">5.1 Optional</a>
1) Optional
2) Optional 생성
3) Optional에 보관된 객체에 접근하기
4) Optional의 동등성(equals)

## <a href="5. Optional과 OptionalInt/5.2 Optional의 여러가지 메서드.md" target="_blank">5.2 Optional의 여러가지 메서드</a>
1) map
2) filter
3) flatMap
4) isPresent
5) ifPresent

## <a href="5. Optional과 OptionalInt/5.3 OptionalInt, OptionalLong, OptionalDouble.md" target="_blank">5.3 OptionalInt, OptionalLong, OptionalDouble</a>
1) 기본형 Optional의 생성
2) 기본형 저장값 반환
3) 기본형 Optional의 null처리

---

# 6. Stream의 최종연산

## <a href="6. Stream의 최종연산/6.1 forEach.md" target="_blank">6.1 forEach</a>
1) forEach
2) forEachOrdered

## <a href="6. Stream의 최종연산/6.2 조건검사.md" target="_blank">6.2 조건검사</a>
1) allMatch, anyMatch, noneMatch
2) findFirst, findAny

## <a href="6. Stream의 최종연산/6.3 누적연산.md" target="_blank">6.3 누적연산</a>
1) reduce
2) count, sum, max, min
3) collect

---

# 7. Stream의 최종연산 - collect

## <a href="7. Stream의 최종연산 - collect/7.1 collect와 Collector.md" target="_blank">7.1 collect와 Collector</a>
1) collect
2) Collector
3) Collectors 클래스
4) collect, Collector, Collectors

## <a href="7. Stream의 최종연산 - collect/7.2 Stream을 컬렉션, 배열로 변환.md" target="_blank">7.2 Stream을 컬렉션, 배열로 변환</a>
1) `.collect(...)` - List, Set, Map
2) `toArray(...)`

## <a href="7. Stream의 최종연산 - collect/7.3 통계.md" target="_blank">7.3 통계</a>
1) counting, summingInt, averagingInt, maxBy, minBy
2) summarizingInt

## <a href="7. Stream의 최종연산 - collect/7.4 리듀싱(reducing).md" target="_blank">7.4 리듀싱(reducing)</a>
1) 누적함수만 정의된 reducing
2) 초깃값 + 누적함수
3) 초깃값 + 변환함수 + 누적함수 (map+reduce)

## <a href="7. Stream의 최종연산 - collect/7.5 문자열 결합.md" target="_blank">7.5 문자열 결합</a>
1) joining

---
